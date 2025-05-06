# Class: listform_actions

Provides logic for handling list views and actions in ISPConfig modules, including sorting, filtering, and SQL query customization for data tables.

**Source File:** interface/lib/classes/listform_actions.inc.php

## Properties
- **id**: Internal identifier for the list instance.
- **idx_key**: Field name used as the record index.
- **DataRowColor**: Row color indicator for UI templates.
- **SQLExtWhere**: Custom WHERE clause additions for the SQL query.
- **SQLOrderBy**: Custom ORDER BY clause for the SQL query.
- **SQLExtSelect**: Additional SELECT expressions for the SQL query.
- **sortKeys**: Array of column keys and sort directions for PHP-based sorting.

## Methods
- **_sort($aOne, $aTwo)** (private)
  - Compares two rows according to `sortKeys`, converting size suffixes (kB, MB, GB, TB) for numeric comparison.
- **onLoad()**
  - Loads list definitions, builds templates if needed, and initializes sorting and filtering session settings.
- **prepareDataRow($rec)**
  - Processes and formats a database record for display, handling field substitutions and HTML entities.
- **getQueryString($no_limit = false)**
  - Generates the complete SQL SELECT query for the list, incorporating filters, joins, sorting, and pagination.
- **onShow()**
  - Configures language files, search limits, and template variables, then triggers list rendering.
- **onShowEnd()**
  - Finalizes template defaults and outputs the rendered list page.

## Usage
Used internally by ISPConfig to manage and display data lists with custom sorting, filtering, and SQL customization in module interfaces.
