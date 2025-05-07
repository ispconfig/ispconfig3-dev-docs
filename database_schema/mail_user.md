# mail_user

## Description
This table stores information about email user accounts in ISPConfig. It contains all the configuration details for individual mailboxes, including authentication credentials, quotas, and service settings.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| mailuser_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this mail user |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the mail server where this account is hosted |
| email | varchar(255) | Full email address of the user |
| login | varchar(255) | Login name for the account |
| password | varchar(255) | Encrypted password for the account |
| name | varchar(255) | Full name of the user |
| uid | int(11) | System user ID for mail storage |
| gid | int(11) | System group ID for mail storage |
| maildir | varchar(255) | Path to the mailbox directory |
| quota | bigint(20) | Mailbox quota in bytes |
| cc | varchar(255) | Carbon copy email address |
| homedir | varchar(255) | Home directory path |
| maildir_format | varchar(255) | Format of the maildir |
| postfix | enum('y','n') | Whether Postfix delivery is enabled |
| disableimap | enum('y','n') | Whether IMAP access is disabled |
| disablepop3 | enum('y','n') | Whether POP3 access is disabled |
| disabledeliver | enum('y','n') | Whether mail delivery is disabled |
| disablesmtp | enum('y','n') | Whether SMTP access is disabled |
| autoresponder | enum('y','n') | Whether autoresponder is enabled |
| autoresponder_start_date | datetime | Start date for autoresponder |
| autoresponder_end_date | datetime | End date for autoresponder |
| autoresponder_text | mediumtext | Text content of the autoresponder message |
| autoresponder_subject | varchar(255) | Subject line for autoresponder messages |
| move_junk | enum('y','n') | Whether to move spam to junk folder |
| custom_mailfilter | mediumtext | Custom mail filter rules |
| policy_id | int(11) | ID of the spam policy (references spamfilter_policy) |
| purge_trash_days | int(11) | Days after which trash is purged |
| purge_junk_days | int(11) | Days after which junk mail is purged |
| vacation | enum('y','n') | Whether vacation message is enabled |
| vacation_start_date | datetime | Start date for vacation message |
| vacation_end_date | datetime | End date for vacation message |
| vacation_subject | varchar(255) | Subject line for vacation messages |
| vacation_text | mediumtext | Text content of the vacation message |
| domain | varchar(255) | Domain part of the email address |
| active | enum('y','n') | Whether this account is active |
| domain_id | int(11) | ID of the mail domain (references mail_domain) |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `mail_domain` table via the `domain_id` field
- Related to `spamfilter_policy` table via the `policy_id` field

## Notes
- Central table for email user management in ISPConfig
- Contains all information needed for mail delivery and access
- Supports various mail access protocols (IMAP, POP3, SMTP)
- Includes features like autoresponders and vacation messages
- Provides spam handling and custom filter options
- The ISPConfig interface provides tools for creating and managing mail users
- Active flag can be used to temporarily disable accounts without deleting them
- Various disable flags allow for granular control of email services
