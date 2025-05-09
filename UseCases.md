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
