
# User Stories
-------------
1. As a user, I want to be able to select a specific date.
2. As a user, I want to be able to use advanced logical search operators "AND", "OR" and "NOT, so I can browse case rulings more effectively.
3. As a user, I want to be able to costumize the amount of case rulings showing at once, so I can scroll through the main page freely.
4. 3. As a user, I want to be able to have a compact view of the case ruling so I can improve readibilty.
5. As an admin, I want to be able view suggestions while editing case rulings, so I can be more effecient and ensure data normalization.
6. As an admin, I want to filter and see only the records created since a specific date or time period, so I can track activity.
7. As an admin, I want to export to Excel exactly what I’m seeing in the dashboard, so I can analyze or share it externally.
9. As an admin, I want to identify similar or irregular metadata values across legal documents, so I can maintain data consistency.
10. As an admin, I want to select a target value for normalization and see which documents will be affected before confirming.
11. As an admin, I want to adjust the similarity threshold for term clustering, so I can fine-tune the detection of irregular values.
12. 8. As an admin, I want to quickly edit any record from the dashboard list, so I can correct or update data efficiently.

---------------------------------------------------------------------------------------------------------

# Use Cases

## Dashboard


### View Data Over Time
- Actor selects a date range or date.
- System displays a chart of records created per day/week/month or since a specific date.

### Find Rare Attribute Values
- Actor selects an attribute (e.g., “Decisão”).
- System lists the rarest values and their counts.

### Advanced Search/Filter
- Actor enters filter criteria (date, type, etc.).
- System displays matching records.

### Export Current View
- Actor clicks “Export to Excel”.
- System generates and downloads an Excel file with current filters applied.

### Import Excel and View Report
- Actor uploads an Excel file.
- System processes the file and displays a report of changes (created, updated, errors).

### Edit from List
- Actor clicks “Edit” on a record in the list.
- System opens the editing page for that record.


## Editing Page

### Edit Case Ruling
- Actor loads a case ruling.
- Actor types in fields.
- Actor clicks on suggestion.
- System updates the record and confirms success.
