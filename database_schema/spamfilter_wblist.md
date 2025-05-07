# spamfilter_wblist

## Description
This table stores whitelist and blacklist entries for the spam filter system in ISPConfig, allowing specific email addresses or domains to be explicitly allowed or blocked.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| wblist_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this entry |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server this entry applies to |
| wb | enum('W','B') | Type of entry: 'W' for whitelist, 'B' for blacklist |
| rid | int(11) | Recipient ID (typically references spamfilter_users) |
| email | varchar(255) | Email address or domain pattern to whitelist/blacklist |
| priority | int(11) | Priority of this rule (lower number = higher priority) |
| active | enum('y','n') | Whether this entry is active |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `spamfilter_users` table via the `rid` field

## Notes
- Used for explicitly allowing (whitelisting) or blocking (blacklisting) specific senders
- Can be applied at the domain level (e.g., @example.com) or specific email addresses
- Works in conjunction with the spam scoring system to override automatic classifications
- Particularly useful for preventing false positives or negatives in spam detection
- Priority field allows for resolving conflicts when multiple rules might apply
