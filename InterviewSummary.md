# 📝 Interviews with STJ Employees

Summary of the the meetings with different employees of the Supremo Tribunal de Justiça undertaken on the 14th of May with the Library team and 15th of May with STJ judges. 

The first interview conducted was with the Librarian team at STJ led by André Capricho. They are responsible for creating new case rulings assigned by the STJ and of editing the existing case rulings that are viewed on Juris meaning they used the back office interface on a day to day basis. The last meeting with the judges was mostly focused on the browsing aspect of the application.

The way they receive the case rulings to be created is through email in a picture of the form the Courts use that contains all the case rulings metada and summary in the email itself.

The most signficant discovery from the interview is that both the librarians and the judges pretty much do not use Juris, the entire team dislikes it and finds its current version unpratical and not intuitive for various reasons.
Instead the team currently uses IBM's Lotus Notes for creating and editing the case rulings and DGDSI (the database Juris fetches from) and ECLI (European Case Law Identifier) to search for the existing case rulings in detriment to Juris because of better UI and features. 


In the meetings we had the opportunity to visualize all these tools, compare them to Juris and discuss what causes the team not to use it. 

### Public Interface 

- **Result Limitations**:  
  JURIS currently shows only **10 results per page**.  
  ➤ This should be **customizable**, allowing users to **scroll through all results**, like in DGSI and ECLI.

- **Calendar Filter**:  
  A feature to **search by exact ruling date** is crucial.  
  ✅ *This feature has already been implemented.*

- **Partial Name Search**:  
  ➤ Add support for **partial matches** in name fields.

- **Improved Term Matching**:  
  ➤ Enhance search to:
  - Find results with **all specified terms**
  - Match terms **regardless of order**
  - Support **simple regex search** (useful for legacy rulings)

- **Boolean Operators**:  
  ➤ Add support for:
  - `"AND"` operator (must-have)  
  - `"OR"` operator (nice-to-have)

- **Process Number Search**:  
  ➤ Needs to be implemented using **Elasticsearch**.

### 🧾 2. Field Redundancy

- **"Area" Field**:  
  ➤ Currently redundant — the selected **"Section"** already determines the area.  
  ➤ Improve UX by **automatically selecting the "Area"** when a section is chosen.

---

## 📷 Tools Observed

During the meetings, the following tools were demonstrated and discussed:

| Tool           | Purpose                              |
|----------------|--------------------------------------|
| **Lotus Notes**| Creating and editing case rulings    |
| **DGDSI**      | Primary case law database            |
| **ECLI**       | Advanced search for legal documents  |
| **JURIS**      | Current system (underutilized)       |

### Ideal Metadata Field Order

- Número de acordão 
- Secção 
- Data 
- Relator 
- Meio Processual

### Useless Fields

- Votação
- Área (Useful for Judges)
- Meio processual (Important for the librarians useless for the judges)
- Jurisprudencia
- Decisao
- Fonte
- Estado

### Case Ruling Display
There was also a lot of feedback regarding case ruling display. For each case ruling, it should be showed in small format:
- Number
- Date
- Reporter
- Summary
- Section
- Descriptors

## Backoffice Improvements

Juris currently duplicates a case ruling once it is edited, this is a major bug to be fixed that compromises data normalization.

Too many fields in the backoffice editing interface, make it more intuitive for the users

Add suggestiongs to the text boxes for the metadata filter editing

Too many descriptors, too much information

Lotus Notes doesn't update all records

Statistics dashboard would be very interesting for the judges

For search purposes, old descriptors should neither be marked nor completely removed

For creation, only use current descriptors, not the complete list

## UI/UX Improvements

Increase text size and shorten the width of the case ruling display as it's difficult to read case rulings due to small text and ver long sentences, compare it to ECLI who does it best 

Show fewer case rulings in demonstration but always keep summary open. Summary is the most important element, followed by section and descriptors
- Decision is not important for search purposes
- Descriptors are of little interest for search

Other minor UI tweaks




