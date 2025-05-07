# mail_content_filter

## Description
This table stores information about content filters for email in ISPConfig. Content filters scan email messages for specific patterns or content and can take actions based on the results.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| content_filter_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this content filter |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the mail server where this filter is applied |
| type | varchar(16) | Type of content filter |
| pattern | varchar(255) | Pattern to match in email content |
| data | varchar(255) | Additional data for the filter |
| action | varchar(255) | Action to take when pattern is matched |
| active | enum('n','y') | Whether this content filter is active |

## Relationships
- Related to `server` table via the `server_id` field

## Notes
- Used for filtering email based on content patterns
- Can be used to block spam, viruses, or other unwanted content
- Patterns can include regular expressions or simple text matches
- Actions may include blocking, quarantining, or tagging messages
- The ISPConfig interface provides tools for creating and managing content filters
- Active flag can be used to temporarily disable filters without deleting them
- Part of the email security and management functionality in ISPConfig
