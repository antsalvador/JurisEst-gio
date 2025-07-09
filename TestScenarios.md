# Test Scenarios

## Dashboard: Export Page – “Export Filtered Data to Excel”

| Syntax    |                                                                                                      |
|-----------|------------------------------------------------------------------------------------------------------|
| Name:     | <table id="export_filtered_data">Export filtered data to Excel</table>                               |
| Scenario: | 1. Admin opens the export dashboard page                                                             |
|           | 2. Admin selects a date range filter (e.g., “since 2024-01-01”)                                      |
|           | 3. Admin selects a rare attribute filter (e.g., “Meio Processual:”)                                  |
|           | 4. System displays a list of records matching the filters                                            |
|           | 5. Admin clicks the “Export to Excel” button                                                         |
|           | 6. System generates and downloads an Excel file                                                      |
|           | 7. System displays a confirmation message that export was successful                                 |
|           | 8. Admin opens the Excel file and verifies it contains only the filtered records                     |


## Dashboard: Import Page – “View Analytical Report After Excel Import”

| Syntax    |                                                                                                     |
|-----------|-----------------------------------------------------------------------------------------------------|
| Name:     | <table id="import_excel_report">View analytical report after Excel import</table>                    |
| Scenario: | 1. Admin opens the export dashboard page                                                             |
|           | 2. Admin clicks the “Import Excel” button and selects a valid Excel file                             |
|           | 3. System uploads and processes the file                                                             |
|           | 4. System displays a detailed analytical report, including:                                          |
|           |    - Number of records created                                                                       |
|           |    - Number of records updated                                                                       |
|           |    - Any errors or warnings                                                                          |
|           |    - List of affected record IDs                                                                     |
|           | 5. Actor reviews the report and confirms the import was successful                                   |


## Dashboard: Filtering – “Advanced Filtering by Date and Attribute”

| Syntax    |                                                                                                     |
|-----------|-----------------------------------------------------------------------------------------------------|
| Name:     | <table id="advanced_filtering">Advanced Filtering by Date and Attribute</table>                     |
| Scenario: | 1. Admin navigates to the dashboard                                                                  |
|           | 2. Admin enters a date filter and selects attribute (e.g., “Decisão: AtypicalDecision”)             |
|           | 3. System shows a filtered list of records matching the criteria                                     |
|           | 4. Admin verifies only relevant records are visible                                                  |


## Dashboard: Analysis – “Rare Attribute Value Discovery”

| Syntax    |                                                                                                     |
|-----------|-----------------------------------------------------------------------------------------------------|
| Name:     | <table id="rare_values">Discover rare attribute values</table>                                      |
| Scenario: | 1. Actor opens the dashboard                                                                        |
|           | 2. Actor selects an attribute (e.g., “Tipo”) from the “Rare Attributes” filter                      |
|           | 3. System lists attribute values sorted by rarity                                                    |
|           | 4. Actor reviews the list and investigates rare or suspicious values                                 |


## Dashboard: Visualization – “View Records Created Over Time”

| Syntax    |                                                                                                     |
|-----------|-----------------------------------------------------------------------------------------------------|
| Name:     | <table id="data_over_time">View records created over time</table>                                   |
| Scenario: | 1. Actor navigates to the dashboard                                                                 |
|           | 2. Actor selects a time period (e.g., last 30 days)                                                 |
|           | 3. System displays a time-series chart of created records by day/week/month                         |
|           | 4. Actor visually analyzes spikes or gaps in data                                                    |


## Dashboard: Quick Edit – “Edit Record from List”

| Syntax    |                                                                                                     |
|-----------|-----------------------------------------------------------------------------------------------------|
| Name:     | <table id="edit_from_list">Edit record from dashboard list</table>                                  |
| Scenario: | 1. Actor views a list of records on the dashboard                                                   |
|           | 2. Actor clicks “Edit” on a specific record                                                          |
|           | 3. System navigates to the edit page for that record                                                |
|           | 4. Actor confirms the record data is pre-loaded and ready for update                                |


## Editing Page – “Modify and Save Case Ruling”

| Syntax    |                                                                                                     |
|-----------|-----------------------------------------------------------------------------------------------------|
| Name:     | <table id="edit_case_ruling">Modify and save case ruling</table>                                    |
| Scenario: | 1. Actor opens the case ruling edit page                                                            |
|           | 2. Actor types or clicks on a suggested normalized value                                             |
|           | 3. Actor clicks “Save”                                                                               |
|           | 4. System updates the record and confirms success                                                    |
|           | 5. Actor refreshes the page and verifies the new values persist                                     |


## Normalization Dashboard – "Normalize Duplicated Metadata Term"

| Syntax    |                                                                                                     |
|-----------|-----------------------------------------------------------------------------------------------------|
| Name:     | <table id="normalize_metadata">Normalize similar metadata values</table>                             |
| Scenario: | 1. Actor opens the Export/Import page                                                                |
|           | 2. Actor selects "Descritores" from the metadata field dropdown in the normalization dashboard       |
|           | 3. System displays clusters of similar terms with their frequencies                                  |
|           | 4. Actor adjusts similarity threshold to 0.85                                                        |
|           | 5. Actor selects irregular value "Direito Penal"                                                     |
|           | 6. Actor selects target value "Direito Criminal" from dropdown                                       |
|           | 7. Actor clicks "Normalizar" button                                                                  |
|           | 8. System displays confirmation modal with affected document count                                   |
|           | 9. Actor confirms normalization                                                                      |
|           | 10. System performs bulk update and displays success message with document link                      |
|           | 11. Actor verifies affected documents through provided link                                          |
