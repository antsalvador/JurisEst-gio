
# User Stories
-------------
1. As a user, I want to be able to select a specific date.
2. As an admin, I want to be able view suggestions while editing case rulings, so I can be more effecient and ensure data normalization.
3. As an admin, I want to filter and see only the records created since a specific date or time period, so I can track activity.
4. As an admin, I want to be able to easily visualize abnormal data attributes, so I can investigate outliers.
6. As an admin, I want to export to Excel exactly what I’m seeing in the dashboard, so I can analyze or share it externally.
7. As an admin, I want to quickly edit any record from the dashboard list, so I can correct or update data efficiently.
8. As an admin, I want to see a detailed report after importing an Excel file, so I know what was updated or added.
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
