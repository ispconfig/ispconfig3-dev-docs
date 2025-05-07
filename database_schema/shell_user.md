# shell_user

## Description
This table stores information about shell users who have SSH access to servers managed by ISPConfig.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| shell_user_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this shell user |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server this shell user belongs to |
| parent_domain_id | int(11) | ID of the parent domain (if applicable) |
| username | varchar(64) | Username for shell access |
| password | varchar(64) | Encrypted password |
| quota_size | bigint(20) | Disk quota size in bytes |
| active | varchar(1) | Whether the shell user is active (Y/N) |
| puser | varchar(64) | System username |
| pgroup | varchar(64) | System group name |
| shell | varchar(255) | Path to the shell executable |
| dir | varchar(255) | Home directory path |
| chroot | varchar(1) | Whether to use chroot environment (Y/N) |
| ssh_rsa | text | SSH RSA public key for key-based authentication |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `web_domain` table via the `parent_domain_id` field (if applicable)

## Notes
- Used for managing SSH access to servers
- Allows for restricted shell access with quotas and chroot
- Supports both password and key-based authentication
- Important for providing secure shell access to clients or administrators
