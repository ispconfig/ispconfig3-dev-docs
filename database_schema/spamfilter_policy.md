# spamfilter_policy

## Description
This table stores spam filter policy configurations used by the mail filtering system in ISPConfig.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this policy |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| policy_name | varchar(64) | Name of the spam filter policy |
| virus_lover | enum('N','Y') | Whether to deliver messages with viruses |
| spam_lover | enum('N','Y') | Whether to deliver spam messages |
| banned_files_lover | enum('N','Y') | Whether to deliver messages with banned file attachments |
| bad_header_lover | enum('N','Y') | Whether to deliver messages with bad headers |
| bypass_virus_checks | enum('N','Y') | Whether to bypass virus checking |
| bypass_spam_checks | enum('N','Y') | Whether to bypass spam checking |
| bypass_banned_checks | enum('N','Y') | Whether to bypass banned file checking |
| bypass_header_checks | enum('N','Y') | Whether to bypass header checking |
| spam_modifies_subj | enum('N','Y') | Whether to modify subject line for spam |
| virus_quarantine_to | varchar(255) | Where to quarantine viruses |
| spam_quarantine_to | varchar(255) | Where to quarantine spam |
| banned_quarantine_to | varchar(255) | Where to quarantine banned files |
| bad_header_quarantine_to | varchar(255) | Where to quarantine bad headers |
| clean_quarantine_to | varchar(255) | Where to quarantine clean messages (if applicable) |
| other_quarantine_to | varchar(255) | Where to quarantine other messages |
| spam_tag_level | decimal(5,2) | Spam score at which to tag messages |
| spam_tag2_level | decimal(5,2) | Secondary spam score for tagging |
| spam_kill_level | decimal(5,2) | Spam score at which to reject messages |
| spam_dsn_cutoff_level | decimal(5,2) | Spam score cutoff for delivery status notifications |
| spam_quarantine_cutoff_level | decimal(5,2) | Spam score cutoff for quarantining |
| addr_extension_virus | varchar(64) | Address extension for viruses |
| addr_extension_spam | varchar(64) | Address extension for spam |
| addr_extension_banned | varchar(64) | Address extension for banned files |
| addr_extension_bad_header | varchar(64) | Address extension for bad headers |
| warnvirusrecip | enum('N','Y') | Whether to warn recipients about viruses |
| warnbannedrecip | enum('N','Y') | Whether to warn recipients about banned files |
| warnbadhrecip | enum('N','Y') | Whether to warn recipients about bad headers |
| newvirus_admin | varchar(64) | Admin to notify about new viruses |
| virus_admin | varchar(64) | Admin to notify about viruses |
| banned_admin | varchar(64) | Admin to notify about banned files |
| bad_header_admin | varchar(64) | Admin to notify about bad headers |
| spam_admin | varchar(64) | Admin to notify about spam |
| spam_subject_tag | varchar(64) | Subject tag for spam |
| spam_subject_tag2 | varchar(64) | Secondary subject tag for spam |
| message_size_limit | int(11) | Maximum message size in bytes |
| banned_rulenames | varchar(64) | Names of banned rules to apply |
| server_id | int(11) | ID of the server this policy applies to |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `spamfilter_users` table which assigns policies to mail users

## Notes
- Used for configuring detailed spam and virus filtering behavior
- Allows for different policies for different users or domains
- Integrates with mail filtering systems like Amavis, SpamAssassin, and ClamAV
- Provides fine-grained control over how to handle different types of problematic emails
