# IndexedDB Workbench

IndexedDB Workbench is a single-page web application that provides a graphical interface for exploring and editing data stored in your browser's IndexedDB databases. It behaves like a lightweight desktop database client so you can inspect object stores, query records with SQL-like statements, and perform CRUD operations without writing custom scripts.

## Features

- **Database discovery** – Enumerates the databases available in your browser and lets you switch between them without reloading the page.
- **Object store browser** – Presents each store's metadata (key path, auto-increment state, indexes, and key/value samples) alongside action buttons for loading, editing, or deleting records.
- **Record explorer** – Renders store contents in a sortable table with pagination, quick search, and limit controls. Rows highlight primary keys, expose inline edit/delete buttons, and support viewing nested JSON structures.
- **SQL-like querying** – Bundles the AlaSQL engine locally so you can run queries such as `SELECT * FROM users WHERE age > 30 ORDER BY lastName`. Queries can reference the currently selected store, the special `records` table, or temporary tables you create on the fly.
- **Filtering & search** – Offers text search, property filters, and sort toggles so you can drill into large datasets without writing SQL.
- **CRUD tooling** – Includes forms for inserting new records, editing existing rows (with key awareness for object stores and key generators), and deleting entries after confirmation prompts.
- **Data export** – Allows exporting the current result set as JSON or CSV files for further analysis in other tools.
- **Offline friendly** – Ships as a standalone HTML file that you can open directly from disk or serve from any static web host—no build step or external CDN required.

## Getting Started

Preview IndexDB Workbench [here ](https://htmlpreview.github.io/?https://github.com/andyflury/IndexedDB-Workbench/blob/main/index.html)

or: 
1. Clone or download this repository.
2. Open `index.html`  
3. Grant the page access to IndexedDB (browsers typically allow this automatically for same-origin pages).
4. Use the sidebar to choose a database, then explore stores, run SQL queries, and modify records as needed.

> **Note:** The application reads and writes data directly within your browser. No information is transmitted to external services.

## Usage Tips

- The SQL editor auto-populates with `SELECT * FROM <active_store>` so you can run quick inspections without typing store names manually.
- When you load a store, the app registers both the selected store and a `records` table with AlaSQL. You can join against additional temporary tables by executing `CREATE TABLE` statements within the SQL runner.
- Editing a record opens a modal that displays the existing payload and key values. Modify the JSON body or key fields and click **Save** to persist changes.
- To insert new data, fill out the **Add Record** form. If the store uses an auto-increment key, leave the key field blank.
- Use the export buttons above the results table to download the current view as CSV or JSON.

## Development Notes

The project intentionally avoids build tooling to remain easy to audit and host. All logic resides in `index.html`, which contains:

- Markup for the layout and modal dialogs
- CSS for a dark-theme data workbench aesthetic
- Vanilla JavaScript modules for database access, state management, data grids, and SQL execution

If you extend the app, consider keeping the single-file philosophy or introducing a minimal bundler (e.g., Vite) with care to preserve offline usability.

## License

This project is released under the MIT License. See [LICENSE](LICENSE) if present, or add one if distributing modified versions.
