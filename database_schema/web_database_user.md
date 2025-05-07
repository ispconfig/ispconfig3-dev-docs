# web_database_user

## Description
This table stores information about database users who have access to databases created for websites hosted in ISPConfig. It tracks usernames, passwords, and access privileges.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| database_user_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this database user |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server where this database user exists |
| database_user | varchar(64) | Username for database access |
| database_password | varchar(64) | Encrypted password for database access |
| database_user_prefix | varchar(30) | Prefix added to the username (for organization) |
| parent_domain_id | int(11) | ID of the parent web domain (references web_domain) |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `web_domain` table via the `parent_domain_id` field
- Referenced by `web_database` table via the `database_user_id` field

## Notes
- Used for managing database users for website databases
- Stores encrypted passwords for security
- Database users can be assigned to multiple databases
- Username prefixes help organize users by client or domain
- The ISPConfig interface provides tools for creating and managing database users
- Permissions for database users are typically managed at the database level
