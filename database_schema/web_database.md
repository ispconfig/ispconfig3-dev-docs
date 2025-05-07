# web_database

## Description
This table stores information about databases created for websites hosted in ISPConfig. It tracks database names, users, and related metadata.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| database_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this database |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server where the database is hosted |
| parent_domain_id | int(11) | ID of the parent web domain (references web_domain) |
| type | varchar(16) | Type of database (e.g., 'mysql', 'postgresql') |
| database_name | varchar(64) | Name of the database |
| database_user_id | int(11) | ID of the primary database user (references web_database_user) |
| database_charset | varchar(64) | Character set of the database |
| remote_access | enum('n','y') | Whether remote access is allowed |
| remote_ips | text | Comma-separated list of IPs allowed for remote access |
| backup_interval | varchar(255) | Backup interval for this database |
| backup_copies | int(11) | Number of backup copies to keep |
| active | enum('n','y') | Whether this database is active |
| backup_format_web | varchar(255) | Format for web backups |
| backup_format_db | varchar(255) | Format for database backups |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `web_domain` table via the `parent_domain_id` field
- Related to `web_database_user` table via the `database_user_id` field

## Notes
- Used for managing databases associated with websites
- Supports different database types like MySQL and PostgreSQL
- Controls access permissions including remote access
- Configures backup settings for the database
- The ISPConfig interface provides tools for creating, managing, and backing up databases
