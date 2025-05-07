# mail_transport

## Description
This table stores information about mail transport routes in ISPConfig. It defines custom routing rules for email delivery, allowing mail to be directed through specific servers or services.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| transport_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this transport |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the mail server where this transport is configured |
| domain | varchar(255) | Domain or email pattern this transport applies to |
| transport | varchar(255) | Transport definition (delivery method and destination) |
| sort_order | int(11) | Order in which transports are processed |
| active | enum('n','y') | Whether this transport is active |

## Relationships
- Related to `server` table via the `server_id` field

## Notes
- Used for defining custom mail routing rules
- Transports define how mail is delivered to specific domains or addresses
- The transport field follows Postfix transport map syntax (e.g., `smtp:[mail.example.com]`)
- Can be used to route mail through specific gateways, relays, or external services
- Sort order determines precedence when multiple transports match
- The ISPConfig interface provides tools for creating and managing mail transports
- Active flag can be used to temporarily disable transports without deleting them
- Particularly useful for complex mail environments with multiple delivery paths
