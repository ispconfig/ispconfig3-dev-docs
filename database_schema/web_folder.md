# web_folder

## Description
This table stores information about protected folders within websites hosted in ISPConfig. It tracks folders that require authentication to access, along with their paths and security settings.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| web_folder_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this folder |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server where this folder exists |
| parent_domain_id | int(11) | ID of the parent web domain (references web_domain) |
| path | varchar(255) | Path to the folder relative to the document root |
| active | enum('n','y') | Whether this protected folder is active |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `web_domain` table via the `parent_domain_id` field
- Related to `web_folder_user` table which contains users who can access this folder

## Notes
- Used for creating password-protected directories within websites
- Typically implemented using HTTP Basic Authentication
- The path is relative to the document root of the parent domain
- Multiple users can be granted access to the same protected folder
- The ISPConfig interface provides tools for creating and managing protected folders
- Commonly used for restricting access to admin areas, staging sites, or private content
