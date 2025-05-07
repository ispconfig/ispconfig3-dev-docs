# mail_mailinglist

## Description
This table stores information about mailing lists hosted in ISPConfig. It tracks email distribution lists that allow sending messages to multiple recipients through a single address.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| mailinglist_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this mailing list |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the mail server where this mailing list is hosted |
| domain | varchar(255) | Domain part of the mailing list address |
| listname | varchar(255) | Name part of the mailing list address |
| email | varchar(255) | Full email address of the mailing list |
| password | varchar(255) | Admin password for the mailing list |
| domain_id | int(11) | ID of the mail domain (references mail_domain) |
| active | enum('n','y') | Whether this mailing list is active |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `mail_domain` table via the `domain_id` field

## Notes
- Used for managing email distribution lists
- Mailing lists allow sending messages to multiple recipients through a single address
- Typically implemented using software like Mailman or Majordomo
- The email field contains the full address (listname@domain)
- The ISPConfig interface provides tools for creating and managing mailing lists
- Active flag can be used to temporarily disable mailing lists without deleting them
- Password is used for administrative access to the mailing list management interface
