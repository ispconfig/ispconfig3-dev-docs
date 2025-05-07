# mail_get

## Description
This table stores information about external email accounts that are retrieved and imported into ISPConfig mailboxes. It allows fetching mail from external POP3 or IMAP servers.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| mailget_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this mail retrieval account |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the mail server where retrieved mail is stored |
| type | varchar(255) | Type of retrieval protocol (POP3, IMAP) |
| source_server | varchar(255) | Hostname or IP of the source mail server |
| source_username | varchar(255) | Username for the source mail server |
| source_password | varchar(255) | Password for the source mail server |
| source_delete | enum('n','y') | Whether to delete messages from source after retrieval |
| source_mailbox | varchar(255) | Mailbox name on the source server (for IMAP) |
| destination | varchar(255) | Destination email address where mail is delivered |
| active | enum('n','y') | Whether this mail retrieval is active |
| source_port | int(11) | Port number for the source mail server |
| source_ssl | enum('n','y') | Whether to use SSL/TLS for connection |

## Relationships
- Related to `server` table via the `server_id` field
- Conceptually related to `mail_user` table through the destination address

## Notes
- Used for fetching mail from external email accounts
- Supports both POP3 and IMAP protocols for mail retrieval
- Can be configured to delete or keep messages on the source server
- Allows consolidating multiple external accounts into a single ISPConfig mailbox
- The ISPConfig interface provides tools for creating and managing mail retrieval accounts
- Active flag can be used to temporarily disable retrieval without deleting the account
- SSL/TLS options provide secure connections to external mail servers
