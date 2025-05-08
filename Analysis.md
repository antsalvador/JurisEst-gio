# Analysis and Design 



# Editing Page (Admin - Editar Acórdão)



# Export & Import page (Admin - Editar Acórdão)

## **Main Technologies**

- **React** (with Next.js for routing and SSR)
- **TypeScript**
- **Context API** (for form state)
- **Custom hooks** (e.g., useFetch)
- **API routes** (Next.js API, e.g., /api/doc/[id])

## **Main Components & Structure**

- **Page file:** src/pages/editar/avancado/[id].tsx
- **Layout:** Uses DashboardGenericPage for consistent admin look.
- **Data Fetching:** Uses useFetch to get the document data from /api/doc/[id].
- **Form State:** Uses UpdateContext (React Context) to manage changes before saving.
- **Field Editors:** Dynamically renders field editors based on the document schema:
- TextInput, DateInput, ExactInput, GenericInput, ShowCode, etc. (from @/components/dashboardDoc)
- **Field Metadata:** Uses useKeysFromContext to know which fields exist and how to render them.
- **Actions:** Save, Cancel, Delete buttons, which trigger API calls.

## **API Communication**

- **GET /api/doc/[id]**: Fetches the document to edit.
- **PUT /api/doc/[id]**: Saves changes (sends updated fields as JSON).
- **DELETE /api/doc/[id]**: Deletes the document.

**Data Flow:**
1. Page loads, fetches document via useFetch.
1. User edits fields; changes are stored in UpdateContext.
1. On save, sends a PUT request with the changed fields.
1. On delete, sends a DELETE request.

1. 1. Page loads, fetches document via useFetch.
2. 1. User edits fields; changes are stored in UpdateContext.
3. 1. On save, sends a PUT request with the changed fields.
4. 1. On delete, sends a DELETE request.

## **API Communication**

- **GET /api/excel/status**: Fetches current progress of import/export.
- **GET /api/excel/files**: Fetches list of available export/import files.
- **POST /api/excel/run**: Triggers an export or import operation.

For import: sends a FormData with the file.

For export: sends selected fields as query params.

- **GET /api/excel/[id]/[link]**: Downloads a specific file (exported Excel, aggregation, etc).

## **Main Technologies**

- **React** (with Next.js)
- **TypeScript**
- **Custom hooks** (e.g., useFetch)
- **API routes** (Next.js API, e.g., /api/excel/run, /api/excel/files)

**Data Flow:**

1. Page loads, fetches status and file list via useFetch.
2. User selects fields and uploads a file or requests export.
3. On action, sends a POST to /api/excel/run.
4. Progress bars update via polling /api/excel/status.
5. Table updates via polling /api/excel/files.
6. User can download files via links.