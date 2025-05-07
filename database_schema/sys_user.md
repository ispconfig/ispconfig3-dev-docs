# sys_user

## Description
This table stores information about users who can log into the ISPConfig control panel. It contains authentication details, permissions, and user preferences.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| userid | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this user record |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| username | varchar(64) | Username for login |
| passwort | varchar(64) | Encrypted password |
| modules | varchar(255) | Comma-separated list of modules this user has access to |
| startmodule | varchar(255) | Default module to show after login |
| app_module | varchar(255) | Application module this user is associated with |
| language | varchar(2) | Language code for the user interface |
| theme | varchar(32) | Theme selected for the user interface |
| typ | varchar(16) | Type of user (admin, user, etc.) |
| active | tinyint(1) | Whether this user is active (1) or not (0) |
| client_id | int(11) | ID of the client this user belongs to (if applicable) |
| groups | text | Additional groups this user belongs to |
| default_group | int(11) | Default group for this user |
| lost_password_function | tinyint(1) | Whether the lost password function is enabled (1) or not (0) |
| lost_password_hash | varchar(50) | Hash for password reset functionality |
| lost_password_reqtime | datetime | Timestamp of the last password reset request |

## Relationships
- Related to `sys_group` table via the `sys_groupid` field and the `groups` field
- Related to `client` table via the `client_id` field
- Referenced by `sys_session` table for active sessions

## Notes
- Central table for user authentication and authorization in ISPConfig
- Stores encrypted passwords for security
- Controls which modules and functions users can access
- Supports multiple languages and themes for user preferences
- User types determine overall permissions and capabilities
- Active flag can be used to temporarily disable user accounts
