# ISPConfig Form System: Validators

This document lists all available form validator types (`type`) in the ISPConfig tform system, with modern PHP array syntax examples for each.

---

## List of Validator Types

### 1. `NOTEMPTY`
Ensures the field is not empty.
```php
'validators' => [
    [
        'type' => 'NOTEMPTY',
        'errmsg' => 'field_required_error'
    ]
]
```

### 2. `REGEX`
Validates the field using a regular expression.
```php
'validators' => [
    [
        'type' => 'REGEX',
        'regex' => '/^([0-9]{1,5})$/',
        'errmsg' => 'field_error_regex'
    ]
]
```

### 3. `CUSTOM`
Uses a custom PHP class and function for validation.
```php
'validators' => [
    [
        'type' => 'CUSTOM',
        'class' => 'validate_domain',
        'function' => 'web_domain_autosub',
        'errmsg' => 'domain_error_autosub'
    ]
]
```

### 4. `ISPOSITIVE`
Checks if a value is a positive number.
```php
'validators' => [
    [
        'type' => 'ISPOSITIVE',
        'errmsg' => 'value_must_be_positive'
    ]
]
```

### 5. `UNIQUE`
Checks if the value is unique in the database.
```php
'validators' => [
    [
        'type' => 'UNIQUE',
        'errmsg' => 'value_must_be_unique'
    ]
]
```

### 6. `ISASCII`
Ensures the value contains only ASCII characters.
```php
'validators' => [
    [
        'type' => 'ISASCII',
        'errmsg' => 'Value must be ASCII only.'
    ]
]
```

### 7. `ISDOMAIN`
Checks if the value is a valid domain name.
```php
'validators' => [
    [
        'type' => 'ISDOMAIN',
        'errmsg' => 'Invalid domain name.'
    ]
]
```

### 8. `ISEMAIL`
Checks if the value is a valid email address (with stricter rules, e.g., no plus in local-part).
```php
'validators' => [
    [
        'type' => 'ISEMAIL',
        'errmsg' => 'Invalid email address.'
    ]
]
```

### 9. `ISEMAILADDRESS`
Checks if the value is a valid email address (standard validation).
```php
'validators' => [
    [
        'type' => 'ISEMAILADDRESS',
        'errmsg' => 'Invalid email address.'
    ]
]
```

---

## Notes
- The `errmsg` key specifies the error message or its translation key.
- The `CUSTOM` validator requires a `class` and `function` for custom logic.
- `REGEX` validators require a `regex` pattern.
- Multiple validators can be combined in the same field.

---

This list covers the most common validator types. Additional or module-specific validators may exist. For advanced usage, refer to the respective `.tform.php` files in each module.
