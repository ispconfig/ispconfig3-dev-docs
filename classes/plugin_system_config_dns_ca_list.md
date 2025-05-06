# Class: plugin_system_config_dns_ca_list

Extends `plugin_base` to manage the list view and actions for DNS Certificate Authorities (CAs) in ISPConfig's system configuration. Supports displaying, editing, and deleting CA records.

## Properties
- **module, form, tab, record_id, formdef, options**: Used for form handling and context.

## Methods
- **onShow()**
  - Displays the list of DNS CA records, loads the appropriate language file, and processes edit or delete actions (admin only).

## Usage
This class is used in the ISPConfig system configuration to allow administrators to view, edit, or delete DNS CA records for SSL management.
