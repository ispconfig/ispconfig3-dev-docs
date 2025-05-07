# spamfilter_users

## Description
This table maps spam filter policies to email users, domains, or email addresses in the ISPConfig mail system.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this record |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server this mapping applies to |
| priority | int(11) | Priority of this policy assignment (lower number = higher priority) |
| policy_id | int(11) | ID of the spam filter policy to apply (references spamfilter_policy) |
| email | varchar(255) | Email address, domain, or pattern this policy applies to |
| fullname | varchar(255) | Full name of the user (if applicable) |
| local | varchar(1) | Whether this is a local user (Y/N) |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `spamfilter_policy` table via the `policy_id` field
- Conceptually related to `mail_user` and `mail_domain` tables through the email field

## Notes
- Used for assigning spam filter policies to specific recipients
- Supports wildcard patterns for applying policies to groups of addresses
- Priority field allows for overlapping rules with clear precedence
- Essential component of the mail filtering system in ISPConfig
- Enables different spam handling policies for different users or domains
