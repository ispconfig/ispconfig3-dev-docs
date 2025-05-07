# client_message_template

## Description
This table stores message templates that can be used for communication with clients in ISPConfig. It contains predefined message content for various types of client notifications.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this template |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| template_type | varchar(255) | Type of message template |
| template_name | varchar(255) | Name of the template |
| subject | varchar(255) | Subject line of the message |
| message | text | Body content of the message |
| active | enum('n','y') | Whether this template is active |

## Relationships
- May be used by various client notification processes

## Notes
- Used for standardizing communication with clients
- Templates can include placeholders that are replaced with actual values
- Supports different types of messages for various notifications
- The ISPConfig interface provides tools for creating and managing message templates
- Helps maintain consistent communication style and content
- Active flag can be used to temporarily disable a template without deleting it
