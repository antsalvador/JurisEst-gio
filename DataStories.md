# Juris Data Normalization Analysis

## Introduction

The objective of this analysis on Juris data is to detect instances where case ruling metadata fields are not properly normalized. Such inconsistencies can compromise the integrity of the application, particularly when users browse case rulings via the search filters.

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

## Available Sheets

```python
xls = pd.ExcelFile(file_path)
xls.sheet_names
```

Returns a list of all available sheets in the Excel file.

## Working with "Meio Processual"

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

### For "Meio Processual - Mostrar"

```python
from rapidfuzz import fuzz
from itertools import combinations

column_name = "Meio Processual - Mostrar"
unique_strings = df_dados[column_name].dropna().unique()
normalized_strings = [s.strip().lower() for s in unique_strings]

threshold = 90
similar_pairs = []
for s1, s2 in combinations(range(len(normalized_strings)), 2):
    score = fuzz.ratio(normalized_strings[s1], normalized_strings[s2])
    if score >= threshold and normalized_strings[s1] != normalized_strings[s2]:
        similar_pairs.append((unique_strings[s1], unique_strings[s2], score))
```

This script identifies string pairs with high similarity, which may represent inconsistent but semantically equivalent entries.

### Output Example

```
'Procedimento ordinário' and 'procedimento ordinario' --> Similarity Score: 95
'DESPACHO' and 'Despacho' --> Similarity Score: 100
'ação penal' and 'Ação Penal' --> Similarity Score: 100
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


