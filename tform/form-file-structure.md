# ISPConfig Form File Configuration

This document describes the structure and conventions of `.tform.php` files in ISPConfig modules, based on actual examples (e.g., `mail_domain.tform.php`).

## Top-Level `$form` Definitions
Each form file sets individual `$form[...]` entries rather than a single array literal:

```php
$form["title"]              = "My Module";           // Form title
$form["description"]        = "...";                // Form description
$form["name"]               = "module_name";         // Unique form identifier
$form["record_name_field"]  = "name";                // Field for record display
$form["action"]             = "module_edit.php";     // Submit handler script
$form["db_table"]           = "module_table";        // Database table
$form["db_table_idx"]       = "id";                  // Primary key column
$form["db_history"]         = "yes";                 // Enable history (yes/no)
$form["tab_default"]        = "main";                // Default tab
$form["list_default"]       = "module_list.php";     // Default list page
$form["auth"]               = "yes";                 // Enable auth check (yes/no)

// Permission presets when creating new records (record_id = 0)
$form["auth_preset"]["userid"]     = 0;
$form["auth_preset"]["groupid"]    = 0;
$form["auth_preset"]["perm_user"]  = 'riud';
$form["auth_preset"]["perm_group"] = 'riud';
$form["auth_preset"]["perm_other"] = '';
```

## Tabs Section
Tabs are configured by assigning to `$form["tabs"]["<tab_name>"]`:

```php
$form["tabs"]["domain"] = [
    'title'    => "Domain",
    'template' => "templates/mail_domain_edit.htm",
    'width'    => 100,                 // optional
    'fields'   => [
        'server_id' => [
            'datatype'   => 'INTEGER',
            'formtype'   => 'SELECT',
            'default'    => '',
            'datasource' => [
                'type'        => 'SQL',
                'querystring' => 'SELECT server_id,server_name ...',
                'keyfield'    => 'server_id',
                'valuefield'  => 'server_name'
            ],
            'value'      => ''             // optional override
        ],
        'domain'    => [
            'datatype'   => 'VARCHAR',
            'formtype'   => 'TEXT',
            'filters'    => [
                ['event'=>'SAVE','type'=>'IDNTOASCII'],
                ['event'=>'SHOW','type'=>'IDNTOUTF8'],
                ['event'=>'SAVE','type'=>'TOLOWER']
            ],
            'validators' => [
                ['type'=>'NOTEMPTY','errmsg'=>'domain_error_empty'],
                ['type'=>'ISDOMAIN','errmsg'=>'domain_error_regex'],
                ['type'=>'CUSTOM','class'=>'validate_mail_transport','function'=>'validate_isnot_mailtransport','errmsg'=>'domain_is_transport']
            ],
            'default'    => '',
            'value'      => ''             // optional override
        ],
        // ... other fields
    ]
];
```

### Field Definition Keys
- **datatype**: `INTEGER`, `DOUBLE`, `CURRENCY`, `VARCHAR`, `TEXT`, `DATE`
- **formtype**: `TEXT`, `TEXTAREA`, `PASSWORD`, `SELECT`, `RADIO`, `CHECKBOX`, `CHECKBOXARRAY`, `FILE`
- **default**: Default value
- **value**: Value override
- **width**: Input width
- **filters**: Array of `['event'=>'SAVE'|'SHOW', 'type'=>'FILTERTYPE']`
- **validators**: Array of `['type'=>'VALIDATORTYPE', 'errmsg'=>'error_key']`
- **datasource**: `['type'=>'SQL','querystring'=>'...','keyfield'=>'...','valuefield'=>'...']`
- **searchable**: `1` (title), `2` (description)

## Workflow
1. `tform->loadFormDef($file)` loads these `$form[...]` entries.
2. `tform->showForm()` renders the tabs and fields.
3. `tform->onSubmit()` validates and saves data.
4. `tform_actions` provides hooks for custom logic.

This structure matches the pattern seen in real ISPConfig form definitions.
