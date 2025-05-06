# ISPConfig Form System: Filters

This document lists common filter types (`type`) available in the ISPConfig tform system, with modern PHP array syntax examples for each.

---

## List of Filter Types

### 1. `IDNTOASCII`
Converts internationalized domain names to ASCII (Punycode) on save.
```php
'filters' => [
    [
        'event' => 'SAVE',
        'type' => 'IDNTOASCII'
    ]
]
```

### 2. `IDNTOUTF8`
Converts ASCII (Punycode) domain names to UTF-8 for display.
```php
'filters' => [
    [
        'event' => 'SHOW',
        'type' => 'IDNTOUTF8'
    ]
]
```

### 3. `TOLOWER`
Converts the value to lowercase on save.
```php
'filters' => [
    [
        'event' => 'SAVE',
        'type' => 'TOLOWER'
    ]
]
```

### 4. `TOUPPER`
Converts the value to uppercase on save.
```php
'filters' => [
    [
        'event' => 'SAVE',
        'type' => 'TOUPPER'
    ]
]
```

### 5. `TOLATIN1`
Converts the value to ISO-8859-1 encoding on save.
```php
'filters' => [
    [
        'event' => 'SAVE',
        'type' => 'TOLATIN1'
    ]
]
```

### 6. `TRIM`
Removes whitespace from the beginning and end of the value on save.
```php
'filters' => [
    [
        'event' => 'SAVE',
        'type' => 'TRIM'
    ]
]
```

### 7. `NOWHITESPACE`
Removes all whitespace characters from the value on save.
```php
'filters' => [
    [
        'event' => 'SAVE',
        'type' => 'NOWHITESPACE'
    ]
]
```

### 8. `STRIPTAGS`
Removes HTML and PHP tags from the value on save.
```php
'filters' => [
    [
        'event' => 'SAVE',
        'type' => 'STRIPTAGS'
    ]
]
```

### 9. `STRIPNL`
Removes newline characters from the value on save.
```php
'filters' => [
    [
        'event' => 'SAVE',
        'type' => 'STRIPNL'
    ]
]
```

### 10. `NORMALIZEPATH`
Normalizes filesystem paths (slashes, dots, etc.) on save.
```php
'filters' => [
    [
        'event' => 'SAVE',
        'type' => 'NORMALIZEPATH'
    ]
]
```

---

## Notes
- The `event` key specifies when the filter is applied: `SAVE` (before saving to DB) or `SHOW` (before displaying to the user).
- Multiple filters can be combined for a single field.
- Filters are useful for normalizing, sanitizing, or formatting user input.

---

For a complete list and advanced usage, see the respective `.tform.php` files in each ISPConfig module.
