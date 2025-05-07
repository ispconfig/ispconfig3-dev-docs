# sys_config

## Description
This table stores system-wide configuration settings for the ISPConfig control panel. It contains key-value pairs for various system parameters that control the behavior of the application.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| config_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this configuration |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server this configuration applies to (0 for global) |
| config_key | varchar(255) | Configuration key name |
| config_value | varchar(255) | Configuration value |

## Relationships
- Related to `server` table via the `server_id` field when server-specific

## Notes
- Central storage for system configuration parameters
- Used by various components of ISPConfig to determine behavior
- Some settings may be global (server_id = 0) while others are server-specific
- Typically managed through the ISPConfig interface rather than direct database access
- Changes to this table may require service restarts to take effect
