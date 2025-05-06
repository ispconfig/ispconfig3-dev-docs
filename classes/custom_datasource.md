# Class: custom_datasource

Provides custom data sources for ISPConfig form fields, such as master templates and DNS server lists.

## Methods
- **master_templates($field, $record)**
  - Returns an array of available master templates for use in forms.
- **dns_servers($field, $record)**
  - Returns an array of available DNS servers, filtered by user permissions and client limits.
