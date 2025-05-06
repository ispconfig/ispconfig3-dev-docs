# ISPConfig tform: Field Settings Reference

This document explains all available field settings for ISPConfig tform definitions. Each field in a tform tab can define a variety of settings to control its behavior, validation, filtering, and display.

---

## Common Field Settings

| Setting         | Type      | Description |
|----------------|-----------|-------------|
| `datatype`     | string    | Underlying data type. Common values: `INTEGER`, `VARCHAR`, `TEXT`, `DATE`, `DATETIME`, `DOUBLE`, `CURRENCY`. |
| `formtype`     | string    | UI element type. E.g. `TEXT`, `SELECT`, `PASSWORD`, `CHECKBOX`, `CHECKBOXARRAY`, `RADIO`, `MULTIPLE`, `DATE`, `DATETIME`. |
| `default`      | mixed     | Default value for the field. |
| `value`        | mixed     | List of possible values (for `SELECT`, `MULTIPLE`, `RADIO`, etc.). Can be an array or a single value. |
| `separator`    | string    | Separator for multiple values (e.g., ","). Used in `MULTIPLE` and `CHECKBOXARRAY`. |
| `validators`   | array     | Array of validator definitions for input validation. |
| `filters`      | array     | Array of filter definitions for value transformation on save/show. |
| `datasource`   | array     | Data source for dynamic value lists. Supports SQL or custom class. |
| `width`        | int       | Display width (optional, for UI). |
| `maxlength`    | int       | Maximum allowed input length. |
| `rows`         | int       | Number of rows (for `TEXTAREA`). |
| `cols`         | int       | Number of columns (for `TEXTAREA`). |
| `readonly`     | bool      | If true, field is read-only. |
| `disabled`     | bool      | If true, field is disabled. |
| `searchable`   | bool      | If true, field can be used in search. |
| `autocomplete` | bool      | If true, enables browser autocomplete. |
| `class`        | string    | CSS class for the field. |
| `id`           | string    | HTML id attribute for the field. |
| `tooltip`      | string    | Tooltip/help text for the field. |
| `tabindex`     | int       | Tab order index for the field. |
| `render_inline`| string    | For `CHECKBOXARRAY` and `RADIO`, controls inline rendering (`y` or `n`). |
| `data-check-fields` | string | Additional client-side validation (used in some arrays). |

---

## Detailed Setting Descriptions

### `datatype`
- **Description:** Sets the base data type for the field as stored in the database.
- **Common values:**
  - `INTEGER`, `DOUBLE`, `CURRENCY`, `VARCHAR`, `TEXT`, `DATE`, `DATETIME`

### `formtype`
- **Description:** Controls the form input type displayed to the user.
- **Common values:**
  - `TEXT`, `PASSWORD`, `SELECT`, `MULTIPLE`, `CHECKBOX`, `CHECKBOXARRAY`, `RADIO`, `DATE`, `DATETIME`, `TEXTAREA`

### `default`
- **Description:** The initial value assigned to the field if no value is provided.

### `value`
- **Description:**
  - For select-like fields, an associative array of possible values.
  - For text fields, can be a default string.

### `separator`
- **Description:** Character used to separate multiple selected values (e.g., `,`).

### `validators`
- **Description:** Array of validator definitions. See [form-validators.md](./form-validators.md) for details and advanced usage.

### `filters`
- **Description:** Array of filter definitions. See [form-filters.md](./form-filters.md) for details and advanced usage.

### `datasource`
- **Description:**
  - Used for dynamic value lists.
  - See the dedicated [Datasource documentation](./form-datasource.md) for advanced usage, SQL/custom examples, and available options.
  - Example for SQL:
    ```php
    'datasource' => [
        'type' => 'SQL',
        'querystring' => 'SELECT id, name FROM table',
        'keyfield' => 'id',
        'valuefield' => 'name'
    ]
    ```
  - Example for custom:
    ```php
    'datasource' => [
        'type' => 'CUSTOM',
        'class' => 'my_class',
        'function' => 'my_function'
    ]
    ```

### `width`, `maxlength`, `rows`, `cols`
- **Description:** UI layout and input restrictions.

### `readonly`, `disabled`, `searchable`, `autocomplete`
- **Description:** Boolean options for UI and behavior.

### `class`, `id`, `tooltip`, `tabindex`
- **Description:** HTML/CSS and accessibility attributes.

### `render_inline`, `data-check-fields`
- **Description:**
  - `render_inline`: For `CHECKBOXARRAY` and `RADIO`, controls whether elements are displayed inline (`y`) or stacked (`n`).
  - `data-check-fields`: Used for additional client-side validation.

---

## Example Field Definition

```php
'domain' => [
    'datatype' => 'VARCHAR',
    'formtype' => 'TEXT',
    'default' => '',
    'filters' => [
        ['event' => 'SAVE', 'type' => 'IDNTOASCII'],
        ['event' => 'SHOW', 'type' => 'IDNTOUTF8'],
        ['event' => 'SAVE', 'type' => 'TOLOWER']
    ],
    'validators' => [
        ['type' => 'NOTEMPTY', 'errmsg' => 'domain_error_empty'],
        ['type' => 'ISDOMAIN', 'errmsg' => 'domain_error_regex'],
        ['type' => 'CUSTOM', 'class' => 'validate_mail_transport', 'function' => 'validate_domain']
    ]
]
```

---

## See Also
- [Form Field Types](./form-field-types.md)
- [Form Validators](./form-validators.md)
- [Form Filters](./form-filters.md)
