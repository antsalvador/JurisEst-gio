
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

# Test Scenarios

## Dashboard Functionality

### Viewing Data Over Time
**Given** records exist with various creation dates,  
**When** the admin selects a specific date range,  
**Then** the chart updates to show only records created within that range.

### Finding Rare Values
**Given** a dataset containing both common and rare attribute values,  
**When** the admin selects a particular attribute (e.g., “Tipo”),  
**Then** the system displays a list sorted by rarity, showing the rarest values first.

### Advanced Filtering
**Given** a collection of diverse records,  
**When** the admin applies one or more filters (e.g., date, type),  
**Then** only records matching those criteria are shown in the table.

### Exporting the Current View
**Given** a filtered dataset visible in the dashboard,  
**When** the admin clicks the “Export to Excel” button,  
**Then** the system generates and downloads an Excel file reflecting the current filtered view.

### Importing Excel and Viewing Report
**Given** a valid Excel file formatted for import,  
**When** the admin uploads the file through the interface,  
**Then** the system processes the file and displays a report detailing created records, updated entries, and any encountered errors.

### Editing from the Record List
**Given** a list of searchable or filtered records,  
**When** the admin clicks the “Edit” button on a specific record,  
**Then** the system navigates to the editing page for that document.

---

## Editing Page Interactions

### Editing and Saving a Case Ruling
**Given** a case ruling loaded in the editing interface,  
**When** the admin modifies the content by clicking on a suggested change or manually editing a field,  
**Then** the updated values are saved successfully and reflected when the page reloads.



| Syntax      |                                                                                                    |
| ----------- | -------------------------------------------------------------------------------------------------- |
| Name:       | <table id="export_filtered_data">Export filtered data to Excel</table>                              |
| Scenario:   | 1. Actor <ins> opens the export dashboard page </ins>                                              |
|             | 2. Actor <ins> selects a date range filter (e.g., “since 2024-01-01”)</ins>                        |
|             | 3. Actor <ins> selects a rare attribute filter (e.g., “Tipo: UnusualType”)</ins>                   |
|             | 4. System displays a list of records matching the filters                                          |
|             | 5. Actor <ins> clicks the “Export to Excel” button</ins>                                           |
|             | 6. System generates and downloads an Excel file                                                    |
|             | 7. Actor opens the Excel file and verifies it contains only the filtered records                   |
|             | 8. System displays a confirmation message that export was successful                               |