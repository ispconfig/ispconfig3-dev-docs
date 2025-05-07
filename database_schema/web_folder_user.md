# web_folder_user

## Description
This table stores information about users who have access to protected folders within websites hosted in ISPConfig. It maps users to protected folders and stores their authentication credentials.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| web_folder_user_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this record |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server where this user exists |
| web_folder_id | int(11) | ID of the protected folder (references web_folder) |
| username | varchar(255) | Username for authentication |
| password | varchar(255) | Encrypted password for authentication |
| active | enum('n','y') | Whether this user is active |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `web_folder` table via the `web_folder_id` field

## Notes
- Used for managing access to password-protected directories
- Stores encrypted passwords for security
- Multiple users can be assigned to the same protected folder
- Users are specific to a particular protected folder and not shared across folders
- The ISPConfig interface provides tools for creating and managing folder users
- Typically implemented using HTTP Basic Authentication in the web server
