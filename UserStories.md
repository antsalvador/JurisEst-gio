
# User Stories
-------------
1. As a user, I want to be able to select a specific date.
2. As an admin, I want to be able view suggestions while editing case rulings, so I can be more effecient and ensure data normalization.
3. As an admin, I want to filter and see only the records created since a specific date or time period, so I can track activity.
4. As an admin, I want to be able to easily visualize abnormal data attributes, so I can investigate outliers.
5. As an admin, I want to export to Excel exactly what I’m seeing in the dashboard, so I can analyze or share it externally.
6. As an admin, I want to quickly edit any record from the dashboard list, so I can correct or update data efficiently.
7. As an admin, I want to see a detailed report after importing an Excel file, so I know what was updated or added.
---------------------------------------------------------------------------------------------------------

# Use Cases

## Dashboard


### View Data Over Time
- Actor selects a date range.
- System displays a chart of records created per day/week/month.

### Find Rare Attribute Values
- Actor selects an attribute (e.g., “Tipo”).
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

---

## Editing Page

### Edit Case Ruling
- Actor loads a case ruling.
- Actor edits fields.
- Actor saves changes.
- System updates the record and confirms success.

### Delete Case Ruling
- Actor clicks “Delete”.
- System asks for confirmation.
- Actor confirms.
- System deletes the record.

---

# Test Scenarios

## Dashboard

### Viewing Data Over Time
- Given records exist with various creation dates,  
  When the admin selects a date range,  
  Then only records from that range are shown in the chart.

### Finding Rare Values
- Given records with common and rare values,  
  When the admin selects an attribute,  
  Then the rarest values are listed first.

### Advanced Filtering
- Given various records,  
  When the admin applies filters,  
  Then only matching records are shown.

### Exporting Current View
- Given a filtered view,  
  When the admin clicks “Export”,  
  Then the downloaded Excel matches the current filters.

### Importing Excel
- Given a valid Excel file,  
  When the admin uploads it,  
  Then a report is shown listing all created/updated records and any errors.

### Editing from List
- Given a list of records,  
  When the admin clicks “Edit”,  
  Then the editing page for that record opens.

---

## Editing Page

### Editing and Saving
- Given a case ruling,  
  When the admin edits and saves,  
  Then the changes are persisted and shown on reload.

### Editing and Cancelling
- Given a case ruling,  
  When the admin edits and cancels,  
  Then no changes are saved.

### Deleting
- Given a case ruling,  
  When the admin deletes and confirms,  
  Then the record is removed from the database.


