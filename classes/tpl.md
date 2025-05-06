# Class: tpl

Implements the vlibTemplate engine for ISPConfig. Handles template parsing, variable assignment, loops, includes, and template logic.

**Source File:** interface/lib/classes/tpl.inc.php

## Properties
- **OPTIONS**: Configuration options (e.g., MAX_INCLUDES, TEMPLATE_DIR, CACHE settings).
- **ESCAPE_TAGS**: Definitions for escaping strategies (html, url, rawurl, etc.).
- **FORMAT_TAGS**: Definitions for formatting functions (strtoupper, ucfirst, etc.).
- **allowed_if_ops**: Supported comparison operators for `<tmpl_if>` tags.
- **allowed_loop_dbs**: Supported database types for `setDbLoop()` (MYSQL, POSTGRESQL, etc.).

## Methods
- **newTemplate($tmplfile)**: Initialize a new template file and clear previous state.
- **setVar($k, $v = null, $encode = false)**: Assign variable(s) for `{tmpl_var}` usage.
- **unsetVar(...$vars)**: Remove one or more template variables.
- **getVar($var)** / **getVars()**: Retrieve a single or all assigned variables.
- **setContextVars()**: Assign global context variables.
- **setLoop($k, $v)**: Assign array data for `<tmpl_loop>` iteration.
- **setDbLoop($loopname, $result, $db_type)**: Populate loop from a database result.
- **newLoop($loopname)** / **addRow($row, $loopname)** / **addLoop($loopname)**: 3-step loop construction.
- **unsetLoop(...$loops)**: Remove one or more loops.
- **clearVars()**, **clearLoops()**, **clearAll()**, **reset()**: Clear variables/loops or reset the engine.
- **setInclude($k, $v)** / **setPath(...$paths)**: Define dynamic includes and search paths.
- **setUnknowns($mode)**: Control handling of unknown variables.
- **unknownsExist()** / **getUnknowns()** / **unknowns()**: Check and retrieve unknowns after parsing.
- **render()**: Renders the template and returns the output as a string.
- **display()**: Renders and outputs the template directly.

### Internal Parsing Functions
- **_parseIf($varname, $value = null, $op = null, $namespace = null, $format = null)**
- **_parseTag($args)** / **_parseVar($args)** / **_parseLoop($args)**
- **_parseInclude($args)** / **_parseDynInclude($args)**
- **_parseComment($args)** / **_parseHook($args)** / **_parsePhpInclude($args)**

## Usage
Used by ISPConfig to render HTML templates, inject data, and manage dynamic content via loops, conditionals, and includes.

## Notes
- Many methods are internal (prefixed with `_parse...`). Use public methods for template interaction.
- See also: [template-logic.md](../tform/template-logic.md)
