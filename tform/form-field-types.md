# ISPConfig Form System: Field Types

This document lists all available form field types (`formtype`) in the ISPConfig tform system. Each field type is shown with a short description and a code example as found in typical `.tform.php` files, using modern PHP array syntax.

---

## List of Field Types

### 1. `TEXT`
Single-line text input field.
```php
'fieldname' => [
    'datatype' => 'VARCHAR',
    'formtype' => 'TEXT',
    'default' => '',
    'validators' => [],
    'value' => ''
]
```

### 2. `TEXTAREA`
Multi-line text input field.
```php
'fieldname' => [
    'datatype' => 'TEXT',
    'formtype' => 'TEXTAREA',
    'default' => '',
    'validators' => [],
    'value' => ''
]
```

### 3. `CHECKBOX`
Single checkbox input.
```php
'fieldname' => [
    'datatype' => 'VARCHAR',
    'formtype' => 'CHECKBOX',
    'default' => 'n',
    'value' => ['y' => 'Yes', 'n' => 'No']
]
```

### 4. `CHECKBOXARRAY`
Multiple checkbox inputs (array of checkboxes).
```php
'fieldname' => [
    'datatype' => 'VARCHAR',
    'formtype' => 'CHECKBOXARRAY',
    'default' => '',
    'value' => ['option1' => 'Option 1', 'option2' => 'Option 2']
]
```

### 5. `SELECT`
Dropdown select field.
```php
'fieldname' => [
    'datatype' => 'VARCHAR',
    'formtype' => 'SELECT',
    'default' => '',
    'value' => ['option1' => 'Option 1', 'option2' => 'Option 2']
]
```

### 6. `RADIO`
Radio button group.
```php
'fieldname' => [
    'datatype' => 'VARCHAR',
    'formtype' => 'RADIO',
    'default' => '',
    'value' => ['option1' => 'Option 1', 'option2' => 'Option 2']
]
```

### 7. `PASSWORD`
Password input field (masked input).
```php
'fieldname' => [
    'datatype' => 'VARCHAR',
    'formtype' => 'PASSWORD',
    'default' => '',
    'validators' => [],
    'value' => ''
]
```

### 8. `MULTIPLE`
Allows selection of multiple values from a list. Renders as a multi-select dropdown.
```php
'fieldname' => [
    'datatype' => 'VARCHAR',
    'formtype' => 'MULTIPLE',
    'separator' => ',',
    'value' => ['1' => 'Option 1', '2' => 'Option 2', '3' => 'Option 3']
]
```

---

## Template Integration for Form Field Types

Each form field type in ISPConfig must be rendered with the correct matching HTML input element in the template. The `{tmpl_var name='fieldname'}` placeholder will inject only the value or attributes, not the full input element. You are responsible for declaring the correct `<input>`, `<select>`, or `<textarea>` element for each field type in the template.

Below are correct examples for each field type:

### TEXT
A single-line text input field.

**Template Example:**
```html
<div class="form-group">
    <label for="domain" class="col-sm-3 control-label">{tmpl_var name='label_domain_txt'}</label>
    <div class="col-sm-9">
        <input type="text" name="domain" id="domain" value="{tmpl_var name='domain'}" class="form-control" />
    </div>
</div>
```

### PASSWORD
A password input field (masked).

**Template Example:**
```html
<div class="form-group">
    <label for="password" class="col-sm-3 control-label">{tmpl_var name='label_password_txt'}</label>
    <div class="col-sm-9">
        <input type="password" name="password" id="password" value="{tmpl_var name='password'}" class="form-control" autocomplete="new-password" />
    </div>
</div>
```

### SELECT
A dropdown select field.

**Template Example:**
```html
<div class="form-group">
    <label for="server_id" class="col-sm-3 control-label">{tmpl_var name='label_server_id_txt'}</label>
    <div class="col-sm-9">
        <select name="server_id" id="server_id" class="form-control">
            <!-- Options rendered by {tmpl_var name='server_id'} -->
            {tmpl_var name='server_id'}
        </select>
    </div>
</div>
```

### MULTIPLE
A multi-select dropdown (allows multiple selections).

**Template Example:**
```html
<div class="form-group">
    <label for="options" class="col-sm-3 control-label">{tmpl_var name='label_options_txt'}</label>
    <div class="col-sm-9">
        <select name="options[]" id="options" class="form-control" multiple>
            <!-- Options rendered by {tmpl_var name='options'} -->
            {tmpl_var name='options'}
        </select>
    </div>
</div>
```

### CHECKBOX
A single checkbox.

**Template Example:**
```html
<div class="form-group">
    <label class="col-sm-3 control-label">{tmpl_var name='label_active_txt'}</label>
    <div class="col-sm-9">
        <!-- Checkbox rendered by {tmpl_var name='active'} -->
        {tmpl_var name='active'}
    </div>
</div>
```

### CHECKBOXARRAY
A group of checkboxes for multiple options.

**Template Example:**
```html
<div class="form-group">
    <label class="col-sm-3 control-label">{tmpl_var name='label_features_txt'}</label>
    <div class="col-sm-9">
        <!-- Each checkbox rendered by {tmpl_var name='features'} -->
        {tmpl_var name='features'}
    </div>
</div>
```

### RADIO
A group of radio buttons.

**Template Example:**
```html
<div class="form-group">
    <label class="col-sm-3 control-label">{tmpl_var name='label_type_txt'}</label>
    <div class="col-sm-9">
        <!-- Each radio button rendered by {tmpl_var name='type'} -->
        {tmpl_var name='type'}
    </div>
</div>
```

### TEXTAREA
A multi-line text input field.

**Template Example:**
```html
<div class="form-group">
    <label for="notes" class="col-sm-3 control-label">{tmpl_var name='label_notes_txt'}</label>
    <div class="col-sm-9">
        <textarea name="notes" id="notes" class="form-control">{tmpl_var name='notes'}</textarea>
    </div>
</div>
```

---

## Additional Notes
- The `{tmpl_var name='fieldname'}` placeholder is replaced by the actual form field HTML at render time.
- The `{tmpl_var name='label_fieldname_txt'}` placeholder is typically used for the translated label text.
- You can add help text, tooltips, or extra descriptions using additional HTML or `{tmpl_var name='help_fieldname_txt'}` if defined in your language files.
- Template logic (e.g., `<tmpl_if>`, `<tmpl_else>`) can be used to show/hide fields or adjust layout based on user roles or field values.
- For custom layouts, you can wrap fields in additional markup or grid classes as needed.
- Naming of variables is based on the field name, with the prefix `label_` for labels and `help_` for help text. Postfix `_txt` is used for translated text.

---

## Notes
- Some fields may support additional options such as `validators`, `datasource`, or default values.
- For advanced usage, refer to the specific `.tform.php` files in each module.

---

This list serves as a starting point for the ISPConfig Form System documentation. Further documentation will provide details and advanced examples for each field type.
