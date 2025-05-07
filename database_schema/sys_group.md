# sys_group

## Description
This table stores information about user groups in the ISPConfig system. Groups are used for organizing users and controlling access permissions to various resources and functions.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| groupid | int(11) | Primary key |
| name | varchar(64) | Name of the group |
| description | text | Description of the group's purpose |
| client_id | int(11) | ID of the client this group belongs to (if applicable) |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| modules | text | Comma-separated list of modules this group has access to |
| app_module | varchar(255) | Application module this group is associated with |
| active | tinyint(1) | Whether this group is active (1) or not (0) |

## Relationships
- Related to `sys_user` table which contains users that belong to these groups
- Related to `client` table via the `client_id` field

## Notes
- Central to the permission system in ISPConfig
- Used for organizing users and controlling access to system functions
- Groups can be assigned to specific clients for client-level administration
- The modules field determines which parts of the ISPConfig system the group can access
- Permissions are typically managed through the ISPConfig interface rather than direct database access
