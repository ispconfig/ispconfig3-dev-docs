# client_template

## Description
This table stores templates for client settings in ISPConfig. These templates define default limits, permissions, and settings that can be applied when creating new clients.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| template_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this template |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| template_name | varchar(64) | Name of the template |
| template_type | varchar(1) | Type of template (e.g., 'm' for master, 'a' for additional) |
| limit_client | int(11) | Maximum number of clients (for reseller templates) |
| limit_domain | int(11) | Maximum number of domains |
| limit_subdomain | int(11) | Maximum number of subdomains |
| limit_mailbox | int(11) | Maximum number of mailboxes |
| limit_mailalias | int(11) | Maximum number of mail aliases |
| limit_webquota | int(11) | Web space quota in MB |
| limit_mailquota | int(11) | Mail quota in MB |
| limit_database | int(11) | Maximum number of databases |
| limit_cron | int(11) | Maximum number of cron jobs |
| limit_dns_zone | int(11) | Maximum number of DNS zones |
| limit_dns_record | int(11) | Maximum number of DNS records |
| limit_shell_user | int(11) | Maximum number of shell users |
| limit_webdav_user | int(11) | Maximum number of WebDAV users |
| limit_backup | varchar(255) | Backup limitations |
| limit_client_error | enum('n','y') | Whether to show limit errors to the client |
| limit_web_domain | int(11) | Maximum number of web domains |
| limit_web_aliasdomain | int(11) | Maximum number of alias domains |
| limit_web_subdomain | int(11) | Maximum number of web subdomains |
| limit_ftp_user | int(11) | Maximum number of FTP users |
| limit_mail_domain | int(11) | Maximum number of mail domains |
| limit_mail_user | int(11) | Maximum number of mail users |
| limit_mail_forward | int(11) | Maximum number of mail forwards |
| limit_mail_catchall | int(11) | Maximum number of catchall accounts |
| limit_mail_route | int(11) | Maximum number of mail routes |
| limit_mail_filter | int(11) | Maximum number of mail filters |
| limit_mail_wblist | int(11) | Maximum number of mail whitelist/blacklist entries |
| limit_mail_spamfilter | int(11) | Maximum number of spam filter entries |
| limit_mail_quota | int(11) | Mail quota in MB |
| limit_xmpp_domain | int(11) | Maximum number of XMPP domains |
| limit_xmpp_user | int(11) | Maximum number of XMPP users |
| limit_spamfilter_wblist | int(11) | Maximum number of spam filter whitelist/blacklist entries |
| limit_spamfilter_user | int(11) | Maximum number of spam filter users |
| limit_spamfilter_policy | int(11) | Maximum number of spam filter policies |
| limit_aps | int(11) | Maximum number of APS instances |
| limit_traffic_quota | int(11) | Traffic quota in MB |
| limit_openvz_vm | int(11) | Maximum number of OpenVZ VMs |
| limit_openvz_vm_template_id | int(11) | Default OpenVZ VM template ID |
| ssh_chroot | varchar(255) | SSH chroot directory |
| web_php_options | varchar(255) | Available PHP options |
| limit_database_quota | int(11) | Database quota in MB |
| limit_database_user | int(11) | Maximum number of database users |
| limit_ssl | enum('n','y') | Whether SSL is allowed |
| limit_ssl_letsencrypt | enum('n','y') | Whether Let's Encrypt SSL is allowed |
| limit_directive_snippets | int(11) | Maximum number of directive snippets |
| limit_aps_packages | int(11) | Maximum number of APS packages |
| limit_client_dns | int(11) | Maximum number of client DNS records |
| limit_dns_slave_zone | int(11) | Maximum number of DNS slave zones |

## Relationships
- Referenced by `client` table via the `template_master` field
- Referenced by `client_template_assigned` table

## Notes
- Used for standardizing client settings and limits
- Simplifies the process of creating new clients with consistent settings
- Master templates define the base settings for a client
- Additional templates can be applied to modify specific settings
- The ISPConfig interface provides tools for creating and managing client templates
- Templates make it easier to manage different tiers of service or client packages
