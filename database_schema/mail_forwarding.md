# mail_forwarding

## Description
This table stores information about email forwarding rules in ISPConfig. It tracks redirections of email from one address to another, allowing for flexible mail routing.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| forwarding_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this forwarding rule |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the mail server where this forwarding rule is applied |
| source | varchar(255) | Source email address (from) |
| destination | text | Destination email address(es) (to) |
| type | enum('alias','forward','aliasdomain') | Type of forwarding rule |
| active | enum('n','y') | Whether this forwarding rule is active |
| domain_id | int(11) | ID of the mail domain (references mail_domain) |
| allow_send_as | enum('n','y') | Whether to allow sending as this address |
| greylisting | enum('n','y') | Whether greylisting is enabled for this forwarding |
| check_mx_record | enum('n','y') | Whether to check MX records for the destination |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `mail_domain` table via the `domain_id` field

## Notes
- Used for redirecting email from one address to another
- Supports different types of forwarding:
  - 'alias' for email aliases within the same domain
  - 'forward' for forwarding to external addresses
  - 'aliasdomain' for domain-wide aliases
- Can forward to multiple destinations (comma-separated)
- The allow_send_as flag enables sending mail as the source address
- Greylisting provides additional spam protection
- The ISPConfig interface provides tools for creating and managing forwarding rules
- Active flag can be used to temporarily disable forwarding without deleting the rule
