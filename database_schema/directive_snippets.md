# directive_snippets

## Description
This table stores reusable configuration directive snippets for web servers in ISPConfig. These snippets can be applied to websites to customize their server configuration.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| directive_snippet_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this snippet |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| name | varchar(255) | Name of the directive snippet |
| type | varchar(255) | Type of web server (e.g., 'apache', 'nginx') |
| snippet | text | The actual directive code |
| active | enum('n','y') | Whether this snippet is active |
| customer_viewable | enum('n','y') | Whether clients can view this snippet |

## Relationships
- May be referenced by `web_domain` table conceptually when snippets are applied to websites

## Notes
- Used for storing reusable configuration snippets for web servers
- Supports different web server types like Apache and Nginx
- Snippets can be applied to websites to customize their configuration
- The ISPConfig interface provides tools for creating and managing directive snippets
- Customer viewable flag controls whether clients can see and use the snippet
- Useful for implementing common configuration patterns across multiple websites
