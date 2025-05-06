# Class: plugin_dbhistory

Extends `plugin_base` to provide database change history display for ISPConfig records. Shows a table of changes (actions, timestamps, users) for a given record, using the `sys_datalog` table.

## Properties
- **module, form, tab, record_id, formdef, options**: Used for context and form handling.

## Methods
- **onShow()**
  - Displays a table of database changes for the current record, showing action, timestamp, and user. Query differs for admin and non-admin users.

## Usage
This class is used internally by ISPConfig to display a change log for database records in the web interface, helping admins and users track modifications.
