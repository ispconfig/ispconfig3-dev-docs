# Class: plugin_backuplist

Extends `plugin_base` to provide backup functionality for web files and databases in ISPConfig. Handles user-triggered backup requests and integrates with the remote action system.

## Properties
- **module, form, tab, record_id, formdef, options**: Various objects and data used for backup processing and form handling.

## Methods
- **makeBackup(&$message, &$error, $wb)** (protected)
  - Processes backup requests for web files or databases, checks for pending actions, and queues new backup actions as needed.

## Usage
This class is used internally when a user triggers a backup from the ISPConfig interface, ensuring backups are properly queued and processed.
