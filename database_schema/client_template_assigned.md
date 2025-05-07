# client_template_assigned

## Description
This table stores the assignments of client templates to specific clients in ISPConfig. It tracks which templates have been applied to which clients.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| assigned_template_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who created this assignment |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| client_id | int(11) | ID of the client (references client) |
| client_template_id | int(11) | ID of the template (references client_template) |
| assigned_template_type | varchar(1) | Type of assignment (e.g., 'm' for master, 'a' for additional) |

## Relationships
- Related to `client` table via the `client_id` field
- Related to `client_template` table via the `client_template_id` field

## Notes
- Used for tracking which templates are applied to which clients
- Supports both master templates and additional templates
- Master templates define the base settings for a client
- Additional templates can be applied to modify specific settings
- The ISPConfig interface manages these assignments when templates are applied to clients
- Important for maintaining the relationship between templates and clients
