# mail_domain

## Description
This table stores information about mail domains hosted in ISPConfig. It contains configuration details for email domains, including server settings and domain-wide options.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| domain_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this mail domain |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the mail server where this domain is hosted |
| domain | varchar(255) | Domain name (e.g., example.com) |
| active | enum('n','y') | Whether this mail domain is active |
| dkim | enum('n','y') | Whether DKIM signing is enabled for this domain |
| dkim_selector | varchar(255) | DKIM selector for this domain |
| dkim_private | text | DKIM private key |
| dkim_public | text | DKIM public key |
| relay_host | varchar(255) | Relay host for outgoing mail |
| relay_user | varchar(255) | Username for relay authentication |
| relay_pass | varchar(255) | Password for relay authentication |
| relay_port | varchar(255) | Port for relay connection |
| relay_active | enum('n','y') | Whether relay is active for this domain |
| client_id | int(11) | ID of the client who owns this domain |
| disablesmtp | enum('n','y') | Whether SMTP is disabled for this domain |
| disableimap | enum('n','y') | Whether IMAP is disabled for this domain |
| disablepop3 | enum('n','y') | Whether POP3 is disabled for this domain |
| disabledeliver | enum('n','y') | Whether mail delivery is disabled for this domain |
| disablespamfilter | enum('n','y') | Whether spam filtering is disabled for this domain |
| policy_id | int(11) | ID of the spam policy for this domain |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `client` table via the `client_id` field
- Related to `spamfilter_policy` table via the `policy_id` field
- Referenced by `mail_user` table for users in this domain
- Referenced by `mail_forwarding` table for forwards in this domain

## Notes
- Central table for email domain management in ISPConfig
- Controls domain-wide settings for email services
- Supports DKIM (DomainKeys Identified Mail) for email authentication
- Can be configured to relay mail through external SMTP servers
- The ISPConfig interface provides tools for creating and managing mail domains
- Active flag can be used to temporarily disable domains without deleting them
- Various disable flags allow for granular control of email services
