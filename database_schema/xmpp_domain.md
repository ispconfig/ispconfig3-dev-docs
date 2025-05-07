# xmpp_domain

## Description
This table stores information about XMPP (Jabber) domains hosted in ISPConfig. It tracks domains that are configured for XMPP messaging services.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| domain_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this XMPP domain |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server where this XMPP domain is hosted |
| domain | varchar(255) | Domain name for XMPP service |
| management_method | varchar(255) | Method used to manage this domain |
| registration | enum('n','y') | Whether user registration is allowed |
| active | enum('n','y') | Whether this XMPP domain is active |

## Relationships
- Related to `server` table via the `server_id` field
- May be related to `mail_domain` or `web_domain` tables conceptually

## Notes
- Used for hosting XMPP (Jabber) instant messaging services
- XMPP is an open standard for messaging and presence information
- Can be used for chat, group chat, voice/video calls, and more
- Registration setting controls whether new users can register accounts
- The ISPConfig interface provides tools for creating and managing XMPP domains
- Typically integrated with an XMPP server like ejabberd or Prosody
