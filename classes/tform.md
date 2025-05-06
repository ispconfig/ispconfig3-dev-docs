# Class: tform

Handles form processing, validation, and database interaction for ISPConfig modules. Supports various data types, form types, and field definitions for dynamic form handling.

**Source File:** interface/lib/classes/tform.inc.php

## Usage
This class is used internally by ISPConfig to manage web forms, validate user input, and interact with database tables for CRUD operations.

## Properties
- Inherits all base form properties and data from `tform_base` (e.g., `formDef`, `table_name`, `errorMessage`).

## Methods
- **checkPerm($record_id, $perm)**
  - Checks if the current user has the specified permission for a record; returns boolean.
- **getNextTab()**
  - Determines the next form tab to display based on session state.
- **getCurrentTab()**
  - Retrieves the currently active form tab from session.
- **isReadonlyTab($tab, $primary_id)**
  - Returns true if the given tab should be rendered read-only for the record.
- **lng($msg)**
  - Translates a label/message using the form-specific wordbook or global language entries.
- **checkClientLimit($limit_name, $sql_where = '')**
  - Verifies client resource limits (e.g., max domains) with optional SQL conditions.
- **checkResellerLimit($limit_name, $sql_where = '')**
  - Verifies reseller resource limits with optional SQL conditions.
- **getDiffRecord($record_old, $record_new)**
  - Computes and returns differences between two record arrays.
- **_getDateHTML($form_element, $default_value)**
  - Generates HTML for DATE input fields using the configured date format.
- **_getDateTimeHTML($form_element, $default_value, $display_seconds=false)**
  - Generates HTML for DATETIME input fields, optionally including seconds.
