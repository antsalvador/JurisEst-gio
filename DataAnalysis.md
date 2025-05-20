# Juris Data Normalization Analysis

## Introduction

The objective of this analysis on Juris data is to detect instances where case ruling metadata fields are not properly normalized. Such inconsistencies can compromise the integrity of the application, particularly when users browse case rulings via the search filters.

The code snippets used here can all be found on [JurisDataAnalysis](!JurisDataAnalysis.ipynb), the entire notebook used for the analysis.

## How Browsing Works in Juris

Browsing in Juris primarily relies on filter textboxes located on the main page. These textboxes are connected to various metadata fields of case rulings such as the judge’s name, voting result, decision type, and procedural means. When users type into a filter textbox, suggestions are presented based on the existing data.

If this metadata is not normalized, users may not see all case rulings corresponding to a given filter value, even when they think they should. This fragmentation arises because identical concepts are represented using different formats or terms.

## Causes of Normalization Issues

These inconsistencies stem from manual data entry by various contributors, leading to variations in the way the same information is recorded since different people can use different terms when actually referring to the same matter. Below are real examples illustrating the types of issues found:

- **Typos**: `"Revita"` → `"Revista"`
- **Old Spelling Agreements**: `"Revista excepcional"` → `"Revista excecional"`
- **Capitalization**: `"DESPACHO"` → `"Despacho"`
- **Punctuation**: `"Conflito."` → `"Conflito"`
- **Rephrasing**: `"Acordão Unimizador"` → `"Acordão de unificação"`
- **Extra Spaces**

Detecting and correcting these normalization issues is key to improving search accuracy and user experience within the Juris application. 
To do this an excel file containing all of Juris data was exported from the application to begin an extensive analysis on the dataset.

## Dataset Loading

```python
import pandas as pd

file_path = "Downloads/JurisDataCleaned.xlsx"
df = pd.read_excel(file_path, engine="openpyxl")
df.head()
```

The Excel file is loaded into a pandas DataFrame using the openpyxl engine.
Afterwards the file is read in order to display the sheet names existent that correspond to each data attribute of a case ruling.

```python
xls = pd.ExcelFile(file_path)
xls.sheet_names
```

It returns a list of all available sheets in the Excel file.

## Selecting which sheets to work on

Only certain sheets are relevant to the analysis and this is because not all case ruling data attributes suffer from normalization issues.
For example the data attribute "Área", which refers to the legal area a case ruling is in, only has a few limited and clearly set options, five to be specific "Área Cível, Área Criminal, Área Social, Contencioso and Formação" making them much more simpler to designate, because of this the legal area and many other data attributes of a case ruling do not contain any issues with its normalization.
Not all fields are this simple however like "Decisão", the decision taken in a case ruling, that can range from "Absolvido", 

We focus on the "Meio Processual" sheet first.

```python
df_dados = pd.read_excel(xls, sheet_name="Meio Processual")
df_dados.columns
```

Returns all the column names. The key columns of interest are:

- `Meio Processual - Mostrar`
- `Meio Processual - Indice`

## String Normalization and Similarity Detection

We apply fuzzy matching using RapidFuzz to identify near-duplicate entries based on similarity scores.

```python
import pandas as pd
from thefuzz import fuzz
from collections import defaultdict, deque


file_path = "Downloads/JurisData.xlsx"  
sheet_name = "Meio Processual"  
column_name = "Meio Processual - Mostrar" 

xls = pd.ExcelFile(file_path)
df_descritores = pd.read_excel(xls, sheet_name=sheet_name)
```

### For "Meio Processual - Mostrar"

Once the unique terms are isolated, a graph structure where each node represents a unique string is constructed, and edges are formed between nodes that are textually similar. To measure this similarity, the script uses the token_sort_ratio metric from the fuzz module (part of the thefuzz library), which compares strings based on their token content, regardless of word order. A similarity threshold of 85% was chosen to capture variations such as typos, case mismatches, inconsistent spacing, or alternate phrasings.

```python
# Extração de strings unicas
all_strings = set()
for val in df_descritores[column_name].dropna():
    for part in str(val).split(","):
        clean = part.strip()
        if clean:
            all_strings.add(clean)

all_strings = list(all_strings)

# Graph de semelhança 
similarity_threshold = 85
graph = defaultdict(set)

print("🔍 Building similarity graph...")
for i in range(len(all_strings)):
    for j in range(i + 1, len(all_strings)):
        a, b = all_strings[i], all_strings[j]
        if fuzz.token_sort_ratio(a, b) >= similarity_threshold:
            graph[a].add(b)
            graph[b].add(a)

```

This script identifies string pairs with high similarity, which may represent inconsistent but semantically equivalent entries.

### Output Example

```
'Procedimento ordinário' and 'procedimento ordinario' --> Similarity Score: 95
'DESPACHO' and 'Despacho' --> Similarity Score: 100
'ação penal' and 'Ação Penal' --> Similarity Score: 100
```
The graph is then traversed using a Breadth-First Search (BFS) algorithm to find connected components, which correspond to clusters of similar strings. Each cluster groups all variations of a particular procedural term that are likely referring to the same concept. For each cluster, the script selects a representative term—typically the shortest or most simple string—as the normalized version. The remaining terms in the cluster are considered similar variants. This choice helps ensure consistency and readability in the filtered metadata. 

```python
# Encontrar clusters
visited = set()
clusters = []

def bfs(start):
    queue = deque([start])
    cluster = set()
    while queue:
        node = queue.popleft()
        if node not in visited:
            visited.add(node)
            cluster.add(node)
            queue.extend(graph[node])
    return cluster

for string in all_strings:
    if string not in visited:
        cluster = bfs(string)
        if cluster:
            clusters.append(cluster)

```
Finally, the clusters are organized into a structured table with two columns “Meio Representativo” and “Meios Semelhantes” to then be exported as CSV file.

```python
# DataFrame final
results = []
for cluster in clusters:
    sorted_cluster = sorted(cluster, key=lambda x: (len(x), x.lower()))
    representative = sorted_cluster[0]
    similar = [s for s in sorted_cluster if s != representative]
    results.append({
        "Meio Representativo": representative,
        "Meios Semelhantes": ", ".join(similar)
    })

# Resultados são salvos, ordenados por ordem alfabética e exportados como clusterDescritores
final_df = pd.DataFrame(results)
final_df.sort_values(by="Meio Representativo", inplace=True)


final_df.to_csv("clustersMeioProcessual.csv", index=False)
print("✅ Done! Results saved to 'clustersMeioProcessual.csv'")
```

### Repeat for "Meio Processual - Indice"

```python
column_name = "Meio Processual - Indice"
unique_strings = df_dados[column_name].dropna().unique()
normalized_strings = [s.strip().lower() for s in unique_strings]

similar_pairs = []
for s1, s2 in combinations(range(len(normalized_strings)), 2):
    score = fuzz.ratio(normalized_strings[s1], normalized_strings[s2])
    if score >= threshold and normalized_strings[s1] != normalized_strings[s2]:
        similar_pairs.append((unique_strings[s1], unique_strings[s2], score))
```

This validates whether indexed representations are also suffering from inconsistency.

## Conclusion

This analysis highlights:

- Frequent inconsistencies in naming due to typos, formatting, and spelling variants.
- Effective use of fuzzy string matching to uncover problematic entries.
- High potential for improving data quality through normalization mappings.

Future work should include:
- Implementing automatic mapping for exact matches and high-confidence fuzzy matches.
- Manual review pipelines for ambiguous or low-confidence matches.
- Exporting cleaned and normalized metadata for application integration.


