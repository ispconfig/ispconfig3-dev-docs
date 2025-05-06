# Class: plugin_backuplist_mail

Extends `plugin_base` to provide mail backup and restore functionality in ISPConfig. Handles backup listing, language file loading, and user-initiated restore actions for mail backups.

## Properties
- **module, form, tab, record_id, formdef, options**: Used for backup processing and form handling.

## Methods
- **onShow()**
  - Displays the mail backup list, loads the appropriate language file, and processes restore actions triggered by the user.

## Usage
This class is used internally by ISPConfig to manage mail backup listings and user-triggered mail restore operations in the web interface.
