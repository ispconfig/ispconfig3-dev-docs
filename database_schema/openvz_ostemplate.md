# openvz_ostemplate

## Description
This table stores information about OpenVZ OS templates available in ISPConfig. OS templates are used as base operating system images for creating new OpenVZ virtual containers.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| ostemplate_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this OS template |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| template_name | varchar(255) | Name of the OS template |
| template_file | varchar(255) | Filename of the OS template |
| server_id | int(11) | ID of the server where this OS template is available |
| allservers | enum('y','n') | Whether this template is available on all servers |
| active | enum('y','n') | Whether this OS template is active |
| description | text | Description of the OS template |

## Relationships
- Related to `server` table via the `server_id` field

## Notes
- Used for managing OS templates for OpenVZ virtual containers
- Templates are base operating system images for creating new containers
- Can be configured to be available on specific servers or all servers
- The ISPConfig interface provides tools for managing OS templates
- Active flag can be used to temporarily disable templates without removing them
- Part of the virtualization management functionality in ISPConfig
- OpenVZ is a container-based virtualization technology for Linux
- Common templates include various Linux distributions like CentOS, Debian, Ubuntu, etc.
