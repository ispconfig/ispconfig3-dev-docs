# Class: tform_base

Base class for form handling in ISPConfig. Defines the structure, validation, and processing of forms.

**Source File:** interface/lib/classes/tform_base.inc.php

## Properties
- **tableDef**: Definition of the database table fields.
- **action**: Current action (`INSERT`, `UPDATE`).
- **table_name**: Name of the database table.
- **table_index**: Primary key field of the table.
- **debug**: Debug flag (0/1) to output diagnostic information.
- **errorMessage**: Collected error messages during validation.
- **dateformat**, **datetimeformat**: Date and datetime display formats.
- **formDef**: Loaded form definition array.
- **wordbook**: Language translations for form labels and hints.
- **module**: Optional module path for template resolution.
- **primary_id**, **primary_id_override**: Record identifier management.
- **diffrec**: Array of field differences for history logging.

## Methods
- **loadFormDef($file, $module = '')**
  - Loads form definition file, populates `formDef`, initializes templates, and language.
- **decode($record, $tab)**
  - Converts raw record data into display-ready values for a specific tab.
- **getDatasourceData($field, $record)**
  - Retrieves key=>value pairs for fields defined with a datasource.
- **applyValueLimit($formtype, $limit, $values, $current_value = '')**
  - Applies value limits to selectable form fields.
- **getHTML($record, $tab, $action = 'NEW')**
  - Prepares HTML-ready record data for new or edit forms.
- **encode($record, $tab, $dbencode = true)**
  - Encodes and validates record data before database storage.
- **filterField($field_name, $field_value, $filters, $filter_event)**
  - Applies configured filters on a field during `SAVE` or `SHOW`.
- **validateField($field_name, $field_value, $validators)**
  - Runs validators on a field value and appends to `errorMessage`.
- **getSQL($record, $tab, $action = 'INSERT', $primary_id = 0, $sql_ext_where = '')**
  - Generates the SQL INSERT or UPDATE statement for the record.
- **showForm()**
  - Renders the form tabs and fields based on `formDef`.
- **getDataRecord($primary_id)**
  - Retrieves a database record by primary key with permission SQL.
- **datalogSave($action, $primary_id, $record_old, $record_new)**
  - Saves history of data changes to the audit (datalog) table.
- **getAuthSQL($perm, $table = '', $userid = NULL, $groups = NULL)**
  - Builds SQL condition for record-level permissions.
- **dbg($array_data)**
  - Outputs debugging information for arrays.

## Usage
Used by tform controllers to load definitions, render forms, validate input, generate SQL, and persist form data with history and permissions.
