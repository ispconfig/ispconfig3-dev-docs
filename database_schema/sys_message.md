# sys_message

## Description
This table stores system messages and notifications that are displayed to users in the ISPConfig control panel. It handles internal communication between administrators and users.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(11) | Primary key |
| sender_id | int(11) | ID of the user who sent the message |
| recipient_id | int(11) | ID of the user who receives the message |
| subject | varchar(255) | Subject line of the message |
| message | text | Content of the message |
| tstamp | int(11) | Unix timestamp when the message was sent |
| sys_userid | int(11) | System user ID associated with this message |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server this message relates to (if applicable) |
| state | varchar(1) | State of the message: 'n' (new), 'r' (read), etc. |

## Relationships
- Related to `sys_user` table via the `sender_id` and `recipient_id` fields
- Related to `server` table via the `server_id` field (if applicable)

## Notes
- Used for internal messaging within the ISPConfig system
- Enables communication between administrators and users
- Messages appear in the user's dashboard or notification area
- Can be used for system notifications, alerts, or general communication
- The ISPConfig interface provides a message center for reading and sending messages
