# ISPConfig tform: Datasource Field Setting

This document provides a detailed explanation of the `datasource` field setting in ISPConfig tform definitions. The `datasource` setting enables fields to populate their options dynamically, typically for `SELECT`, `MULTIPLE`, `RADIO`, and similar field types.

---

## What is a Datasource?
A `datasource` allows a form field to retrieve its available options from a dynamic source, such as a database query or a custom PHP function. This is essential for forms where the available choices may change over time (e.g., list of servers, clients, or domains).

---

## Datasource Structure
A datasource is defined as an associative array with at least a `type` key. There are two main types:
- `SQL`: Retrieve options from a database query.
- `CUSTOM`: Retrieve options from a custom PHP class and function.

### 1. SQL Datasource
Populates field options using a SQL query.

**Required keys:**
- `type`: Always `'SQL'`.
- `querystring`: The SQL query to execute. You can use placeholders (see below).
- `keyfield`: The field from the result set to use as the option value.
- `valuefield`: The field from the result set to use as the option label.

**Example:**
```php
'datasource' => [
    'type' => 'SQL',
    'querystring' => 'SELECT `server_id`, `server_name` FROM `server` WHERE `mail_server` = 1 ORDER BY `server_name`',
    'keyfield' => 'server_id',
    'valuefield' => 'server_name'
]
```

**Placeholders available in `querystring`:**
- `{USERID}`: Current user's ID
- `{GROUPID}`: Current user's default group ID
- `{GROUPS}`: Current user's groups
- `{RECORDID}`: The record's primary key value
- `{AUTHSQL}`: Authorization SQL for current user
- `{AUTHSQL::table}`: Authorization SQL for a specific table

**How it works:**
- The query is executed when the form is loaded.
- Each row produces an option. The value is taken from `keyfield`, and the label from `valuefield`.

---

### 2. CUSTOM Datasource
Populates field options by calling a custom PHP class and function.

**Required keys:**
- `type`: Always `'CUSTOM'`.
- `class`: Name of the PHP class to use.
- `function`: Name of the method to call.

**Example:**
```php
'datasource' => [
    'type' => 'CUSTOM',
    'class' => 'my_custom_class',
    'function' => 'get_options'
]
```

- The specified class and function will be called with the field definition and current record as arguments.
- The function should return an associative array of options (`key => value`).

---

## Combining with Static Values
You can combine a `datasource` with a static `value` array. Static values will be merged with the dynamic options.

**Example:**
```php
'value' => [0 => 'Please select'],
'datasource' => [ ... ]
```

---

## Example: Complete Field with SQL Datasource
```php
'client_id' => [
    'datatype' => 'INTEGER',
    'formtype' => 'SELECT',
    'default' => '',
    'value' => [0 => 'Select Client'],
    'datasource' => [
        'type' => 'SQL',
        'querystring' => 'SELECT `client_id`, `contact_name` FROM `client` WHERE {AUTHSQL} ORDER BY `contact_name`',
        'keyfield' => 'client_id',
        'valuefield' => 'contact_name'
    ]
]
```

---

## Example: Complete Field with CUSTOM Datasource
```php
'custom_field' => [
    'datatype' => 'VARCHAR',
    'formtype' => 'SELECT',
    'datasource' => [
        'type' => 'CUSTOM',
        'class' => 'my_custom_class',
        'function' => 'get_options'
    ]
]
```

---

## Notes
- The datasource is evaluated each time the form is loaded (for both new and edit actions).
- If both `value` and `datasource` are set, the arrays are merged (static values first).
- For advanced use, the custom function can use the current record and field definition to filter or adjust the options.

---

## See Also
- [Form Field Settings](./form-field-settings.md)
- [Form Field Types](./form-field-types.md)
