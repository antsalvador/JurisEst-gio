# Analysis and Design 

## Introduction


# Editing Page (Admin - Editar Acórdão)



# Export & Import page (Admin - Editar Acórdão)

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