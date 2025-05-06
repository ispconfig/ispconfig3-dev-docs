# Class: listform

Handles the definition, loading, and rendering of list views in ISPConfig modules.

**Source File:** interface/lib/classes/listform.inc.php

## Methods

- **loadListDef($file, $module = '')**
  - Loads a list definition, initializes datasources, and sets up language and module context.

- **getDatasourceData($field)**
  - Retrieves key=>value pairs for fields with a datasource, processing SQL queries and placeholders.

- **getSearchSQL($sql_where = '')**
  - Builds and returns the SQL WHERE clause based on search values and filtering rules.

- **getPagingValue($key)**
  - Retrieves a specific paging parameter (e.g., current page, limit) from session.

- **getPagingSQL($sql_where = '1')**
  - Generates the SQL fragment for pagination (LIMIT and OFFSET) based on search context.

- **getPagingHTML($vars)**
  - Returns HTML markup for pagination controls using given variables.

- **getPagingHTMLasTXT($vars)**
  - Returns plain-text pagination information for logging or CLI.

- **getSortSQL()**
  - Builds the ORDER BY clause according to sort settings in session and list definition.

- **decode($record)**
  - Formats and converts a database record for display, handling types (dates, booleans, currency).

- **encode($record)**
  - Prepares a record for database operations by escaping, quoting, and formatting fields.

- **lng($msg)**
  - Retrieves a translation from the wordbook or falls back to the global language.

- **escapeArrayValues($search_values)**
  - Escapes HTML entities in search/filter values.

- **search($list_name, $search_prefix = '', $idx_key = 'id')**
  - Processes search/filtering for a list view, updating session state as needed.

## Properties

- **debug**: Debug flag for verbose output.
- **errorMessage**: Contains the last error message.
- **listDef**: Array of the current list definition.
- **searchValues**: Array of active search and filter values.
- **pagingHTML**: HTML string for pagination controls.
- **pagingValues**: Internal storage for paging parameters.
- **searchChanged**: Indicates if search parameters have been modified.
- **module**: Current module context for the list.
- **wordbook**: Array of translations for list labels and messages.

## Notes
- Used internally by list views and plugins to render tabular data.
- See also: [listform_tpl_generator](./listform_tpl_generator.md)
