# ftp_user

## Description
This table stores information about FTP users who have access to websites hosted in ISPConfig. It tracks usernames, passwords, and access permissions for FTP accounts.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| ftp_user_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this FTP user |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server where this FTP user exists |
| parent_domain_id | int(11) | ID of the parent web domain (references web_domain) |
| username | varchar(64) | Username for FTP access |
| password | varchar(64) | Encrypted password for FTP access |
| quota_size | bigint(20) | Disk quota size in bytes |
| active | enum('n','y') | Whether this FTP user is active |
| uid | varchar(64) | System user ID for file ownership |
| gid | varchar(64) | System group ID for file ownership |
| dir | varchar(255) | Home directory path for this FTP user |
| quota_files | int(11) | Maximum number of files allowed |
| ul_ratio | int(11) | Upload ratio for quota calculation |
| dl_ratio | int(11) | Download ratio for quota calculation |
| ul_bandwidth | int(11) | Upload bandwidth limit in KB/s |
| dl_bandwidth | int(11) | Download bandwidth limit in KB/s |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `web_domain` table via the `parent_domain_id` field

## Notes
- Used for managing FTP access to websites
- FTP users can be restricted to specific directories
- Quota settings control disk space usage
- Bandwidth settings can limit transfer speeds
- The ISPConfig interface provides tools for creating and managing FTP users
- Active flag can be used to temporarily disable FTP access without deleting the account
- UID and GID control file ownership for uploaded files
- Important for website content management and file uploads
