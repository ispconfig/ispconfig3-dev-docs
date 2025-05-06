# Class: plugin_directive_snippets

Extends `plugin_base` to manage web server directive snippets for ISPConfig. Handles displaying and updating selectable directive snippets for web domains in the user interface.

## Properties
- **module, form, tab, record_id, formdef, options**: Used for form handling and context.

## Methods
- **onShow()**
  - Displays a list of available directive snippets for the current server type, marks the selected snippet, and loads the appropriate language file.
- **onUpdate()**
  - Updates the selected directive snippet for a domain when changed by the user.

## Usage
This class is used internally by ISPConfig to allow users to select and apply web server directive snippets to their domains via the web interface.
