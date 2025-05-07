# client_circle

## Description
This table stores information about client circles in ISPConfig. Client circles are groupings of clients that allow for shared resources or permissions between related clients.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| circle_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this circle |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| circle_name | varchar(64) | Name of the client circle |
| client_ids | text | Comma-separated list of client IDs in this circle |
| description | text | Description of the circle's purpose |
| active | enum('n','y') | Whether this circle is active |

## Relationships
- Related to `client` table through the `client_ids` field

## Notes
- Used for grouping related clients together
- Allows for resource sharing or permissions across multiple clients
- Useful for managing multiple clients that belong to the same organization
- The ISPConfig interface provides tools for creating and managing client circles
- Active flag can be used to temporarily disable a circle without deleting it
