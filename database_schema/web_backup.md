# web_backup

## Description
This table stores information about backups of websites and web domains managed by ISPConfig. It tracks backup jobs, their status, and related metadata.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| backup_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this backup |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server where the backup was created |
| parent_domain_id | int(11) | ID of the domain being backed up (references web_domain) |
| backup_type | varchar(64) | Type of backup (e.g., 'web', 'mysql', 'full') |
| backup_mode | varchar(64) | Mode of backup (e.g., 'manual', 'automatic') |
| tstamp | int(11) | Unix timestamp when the backup was created |
| filename | varchar(255) | Name of the backup file |
| filesize | bigint(20) | Size of the backup file in bytes |
| backup_destination | varchar(255) | Destination where the backup is stored |
| backup_password | varchar(255) | Password to encrypt/protect the backup (if applicable) |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `web_domain` table via the `parent_domain_id` field

## Notes
- Used for tracking website and database backups
- Supports different types of backups (web files, databases, or complete backups)
- Can be created manually or automatically through scheduled tasks
- Backup files may be stored locally or on remote storage
- Important for disaster recovery and website restoration
- The ISPConfig interface provides tools for creating and restoring backups
