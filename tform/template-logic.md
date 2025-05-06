# ISPConfig Template Logic Guide

This document explains the logic tags and control structures available in ISPConfig template files (found in `interface/web/<module>/templates/`). These tags allow dynamic rendering, conditional display, and iteration in form and list templates.

---

## Basic Logic Tags

### `<tmpl_if name="..."> ... </tmpl_if>`
- **Description:** Renders content only if the variable is set and evaluates to true.
- **Example:**
```html
<tmpl_if name="is_admin">
    <div class="alert alert-info">You are an admin.</div>
</tmpl_if>
```

### `<tmpl_else>`
- **Description:** Used inside `<tmpl_if>` to specify content to show if the condition is false.
- **Example:**
```html
<tmpl_if name="is_admin">
    <div>Welcome, admin!</div>
<tmpl_else>
    <div>Welcome, user!</div>
</tmpl_if>
```

### `<tmpl_unless name="..."> ... </tmpl_unless>`
- **Description:** Renders content only if the variable is not set or is false.
- **Example:**
```html
<tmpl_unless name="has_domains">
    <div>No domains configured yet.</div>
</tmpl_unless>
```

---

## Comparison and Operators

### `<tmpl_if name="..." op="==" value="..."> ... </tmpl_if>`
- **Description:** Compare a variable to a value.
- **Example:**
```html
<tmpl_if name="status" op="==" value="active">
    <span class="label label-success">Active</span>
<tmpl_else>
    <span class="label label-default">Inactive</span>
</tmpl_if>
```

### Supported Operators
- `==` : equals
- `!=` : not equals
- `>`  : greater than
- `<`  : less than
- `>=` : greater or equal
- `<=` : less or equal

---

## Iteration

### `<tmpl_loop name="..."> ... </tmpl_loop>`
- **Description:** Loops over an array variable, rendering the content for each item.
- **Example:**
```html
<tmpl_loop name="mail_domains">
    <tr>
        <td>{tmpl_var name='domain'}</td>
        <td>{tmpl_var name='status'}</td>
    </tr>
</tmpl_loop>
```

---

## Variable Output

### `{tmpl_var name='...'}`
- **Description:** Outputs the value of the given variable.
- **Example:**
```html
<span>{tmpl_var name='username'}</span>
```

---

## Nesting and Combined Logic
- Logic tags can be nested for complex conditions.
- Loops and conditionals can be combined.

**Example:**
```html
<tmpl_loop name="users">
    <tr>
        <td>{tmpl_var name='username'}</td>
        <td>
            <tmpl_if name="is_admin">
                <span>Admin</span>
            <tmpl_else>
                <span>User</span>
            </tmpl_if>
        </td>
    </tr>
</tmpl_loop>
```

---

## Advanced Template Tags and Features

The ISPConfig template engine (vlibTemplate) supports additional tags and features beyond basic logic. Below is a comprehensive list with examples:

### 1. `<tmpl_var ...>` with Formatting and Escaping
- **Syntax:** `{tmpl_var name='username' format='ucfirst' escape='html'}`
- **Formatting options:** `strtoupper`, `strtolower`, `ucfirst`, `ucwords`, etc.
- **Escaping options:** `html`, `url`, `rawurl`, `sq`, `dq`, `hex`, `hexentity`, `none`
- **Example:**
```html
<span>{tmpl_var name='domain' format='strtoupper' escape='html'}</span>
```

### 2. `<tmpl_if>`, `<tmpl_unless>`, `<tmpl_else>`, `<tmpl_elseif>`
- **Comparison operators:** `==`, `!=`, `>`, `<`, `>=`, `<=`
- **Example:**
```html
<tmpl_if name="status" op="==" value="active">
    <span>Active</span>
<tmpl_elseif name="status" op="==" value="pending">
    <span>Pending</span>
<tmpl_else>
    <span>Inactive</span>
</tmpl_if>
```

### 3. `<tmpl_loop>` with Context Variables
- **Loop context variables:** `__FIRST__`, `__LAST__`, `__INNER__`, `__EVEN__`, `__ODD__`, `__ROWNUM__`
- **Example:**
```html
<tmpl_loop name="users">
    <tr>
        <td>{tmpl_var name='username'}</td>
        <td>
            <tmpl_if name="__FIRST__">First user</tmpl_if>
            <tmpl_if name="__LAST__">Last user</tmpl_if>
            <tmpl_if name="__EVEN__">Even row</tmpl_if>
            <tmpl_if name="__ODD__">Odd row</tmpl_if>
            Row: {tmpl_var name='__ROWNUM__'}
        </td>
    </tr>
</tmpl_loop>
```

### 4. `<tmpl_include file="...">` and `<tmpl_dyninclude name="...">`
- **Static include:**
```html
<tmpl_include file="footer.htm">
```
- **Dynamic include:**
```html
<tmpl_dyninclude name="content_tpl">
```

### 5. `<tmpl_comment>`
- **Block comments in templates:**
```html
<tmpl_comment>
    This section is for developers only and will not appear in output.
</tmpl_comment>
```

### 6. `<tmpl_hook name="...">`
- **Trigger a PHP hook at this point in the template.**
- **Example:**
```html
<tmpl_hook name="before_form_render">
```

### 7. `<tmpl_phpinclude file="...">` *(if enabled)*
- **Directly include a PHP file (requires ENABLE_PHPINCLUDE option):**
```html
<tmpl_phpinclude file="custom.php">
```

---

## Practical Examples

### 1. Show/Hide Field for Admins Only
```html
<tmpl_if name="is_admin">
    <div class="form-group">
        <label for="quota">{tmpl_var name='quota_txt'}</label>
        <div>{tmpl_var name='quota'}</div>
    </div>
</tmpl_if>
```

### 2. Display a Warning if a Value is Exceeded
```html
<tmpl_if name="disk_usage" op=">" value="disk_quota">
    <div class="alert alert-warning">Disk quota exceeded!</div>
</tmpl_if>
```

### 3. List All Items with an Empty State
```html
<tmpl_if name="items">
    <ul>
    <tmpl_loop name="items">
        <li>{tmpl_var name='item_label'}</li>
    </tmpl_loop>
    </ul>
<tmpl_else>
    <div>No items found.</div>
</tmpl_if>
```

### 4. Use `<tmpl_unless>` for Negative Conditions
```html
<tmpl_unless name="has_ssl">
    <div class="alert alert-info">SSL is not enabled for this domain.</div>
</tmpl_unless>
```

---

## Usage Notes and Options

- **Unknown Variables:** The behavior for unknown template variables can be controlled with the `setUnknowns()` method. Options: `ignore`, `remove`, `print`, `leave`, `comment`.
- **Global Variables:** Use `setVar()` to assign variables, and `setLoop()` to assign arrays for looping.
- **Loop Context:** If `LOOP_CONTEXT_VARS` is enabled, special variables (`__FIRST__`, etc.) are available inside loops.
- **Dynamic Includes:** Use `setInclude()` in PHP to define values for `<tmpl_dyninclude>`.
- **Paths:** Use `setPath()` in PHP to set additional include paths for templates.

---

## Example: Dynamic Include and Loop Context
```php
// PHP
$tpl->setInclude('content_tpl', 'form_content.htm');
$tpl->setLoop('users', $usersArray);
```
```html
<!-- Template -->
<tmpl_dyninclude name="content_tpl">
<tmpl_loop name="users">
    <tr>
        <td>{tmpl_var name='username'}</td>
        <td><tmpl_if name="__FIRST__">First</tmpl_if></td>
    </tr>
</tmpl_loop>
```

---

## Best Practices
- Use logic tags to keep templates clean and maintainable.
- You can use `< .... >` Syntax or `{ .... }` Syntax.
- Prefer `{tmpl_var name='fieldname_txt'}` for translated labels.
- Use `<tmpl_if>` and `<tmpl_else>` for user role checks, feature toggles, or conditional help text.
- Combine loops and conditionals for dynamic tables and lists.
- Keep logic in templates simple—complex business logic should remain in PHP.

---

## See Also
- [tpl.inc.php source code](../../interface/lib/classes/tpl.inc.php)
- [Form Field Types](./form-field-types.md)
- [Form Field Settings](./form-field-settings.md)
