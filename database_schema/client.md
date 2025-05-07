# client

## Description
This table stores information about clients (customers) in the ISPConfig system. It contains client details, contact information, and account settings.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| client_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this client record |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| company_name | varchar(64) | Name of the client's company |
| contact_name | varchar(64) | Name of the primary contact person |
| customer_no | varchar(64) | Customer number for reference |
| vat_id | varchar(64) | VAT ID or tax number |
| street | varchar(255) | Street address |
| zip | varchar(32) | ZIP or postal code |
| city | varchar(64) | City |
| state | varchar(64) | State or province |
| country | varchar(64) | Country |
| telephone | varchar(32) | Telephone number |
| mobile | varchar(32) | Mobile phone number |
| fax | varchar(32) | Fax number |
| email | varchar(255) | Email address |
| internet | varchar(255) | Website URL |
| icq | varchar(16) | ICQ number (legacy) |
| notes | text | Additional notes about the client |
| default_mailserver | int(11) | Default mail server ID for this client |
| default_webserver | int(11) | Default web server ID for this client |
| default_dnsserver | int(11) | Default DNS server ID for this client |
| default_dbserver | int(11) | Default database server ID for this client |
| default_slave_dnsserver | int(11) | Default slave DNS server ID for this client |
| usertheme | varchar(32) | User interface theme preference |
| template_master | int(11) | Master template ID |
| template_additional | varchar(255) | Additional template IDs |
| created_at | bigint(20) | Timestamp when the client was created |
| locked | enum('n','y') | Whether the client account is locked |
| canceled | enum('n','y') | Whether the client account is canceled |
| parent_client_id | int(11) | ID of the parent client (for reseller relationships) |
| username | varchar(64) | Username for client login |
| password | varchar(64) | Encrypted password for client login |
| language | varchar(2) | Language preference code |
| limit_client | int(11) | Maximum number of clients this client can create (for resellers) |
| limit_domain | int(11) | Maximum number of domains this client can have |
| limit_subdomain | int(11) | Maximum number of subdomains this client can have |
| limit_mailbox | int(11) | Maximum number of mailboxes this client can have |
| limit_mailalias | int(11) | Maximum number of mail aliases this client can have |
| limit_webquota | int(11) | Web space quota in MB |
| limit_mailquota | int(11) | Mail quota in MB |
| limit_database | int(11) | Maximum number of databases this client can have |
| limit_cron | int(11) | Maximum number of cron jobs this client can have |
| limit_dns_zone | int(11) | Maximum number of DNS zones this client can have |
| limit_dns_record | int(11) | Maximum number of DNS records this client can have |
| limit_shell_user | int(11) | Maximum number of shell users this client can have |
| limit_webdav_user | int(11) | Maximum number of WebDAV users this client can have |
| limit_backup | varchar(255) | Backup limitations |
| limit_client_error | enum('n','y') | Whether to show limit errors to the client |
| limit_web_domain | int(11) | Maximum number of web domains this client can have |
| limit_web_aliasdomain | int(11) | Maximum number of alias domains this client can have |
| limit_web_subdomain | int(11) | Maximum number of web subdomains this client can have |
| limit_ftp_user | int(11) | Maximum number of FTP users this client can have |
| limit_mail_domain | int(11) | Maximum number of mail domains this client can have |
| limit_mail_user | int(11) | Maximum number of mail users this client can have |
| limit_mail_forward | int(11) | Maximum number of mail forwards this client can have |
| limit_mail_catchall | int(11) | Maximum number of catchall accounts this client can have |
| limit_mail_route | int(11) | Maximum number of mail routes this client can have |
| limit_mail_filter | int(11) | Maximum number of mail filters this client can have |
| limit_mail_wblist | int(11) | Maximum number of mail whitelist/blacklist entries |
| limit_mail_spamfilter | int(11) | Maximum number of spam filter entries |
| limit_mail_quota | int(11) | Mail quota in MB |
| limit_xmpp_domain | int(11) | Maximum number of XMPP domains this client can have |
| limit_xmpp_user | int(11) | Maximum number of XMPP users this client can have |
| limit_spamfilter_wblist | int(11) | Maximum number of spam filter whitelist/blacklist entries |
| limit_spamfilter_user | int(11) | Maximum number of spam filter users |
| limit_spamfilter_policy | int(11) | Maximum number of spam filter policies |
| limit_aps | int(11) | Maximum number of APS instances this client can have |
| limit_traffic_quota | int(11) | Traffic quota in MB |
| limit_openvz_vm | int(11) | Maximum number of OpenVZ VMs this client can have |
| limit_openvz_vm_template_id | int(11) | Default OpenVZ VM template ID |
| ssh_chroot | varchar(255) | SSH chroot directory |
| web_php_options | varchar(255) | Available PHP options for this client |
| ssh_rsa | text | SSH RSA public key |
| default_dbserver_mysql | int(11) | Default MySQL database server ID |
| default_webserver_type | varchar(16) | Default web server type |
| default_dnsserver_type | varchar(16) | Default DNS server type |
| limit_database_quota | int(11) | Database quota in MB |
| limit_database_user | int(11) | Maximum number of database users |
| limit_ssl | enum('n','y') | Whether SSL is allowed for this client |
| limit_ssl_letsencrypt | enum('n','y') | Whether Let's Encrypt SSL is allowed for this client |
| limit_directive_snippets | int(11) | Maximum number of directive snippets |
| limit_aps_packages | int(11) | Maximum number of APS packages |
| limit_client_dns | int(11) | Maximum number of client DNS records |
| limit_dns_slave_zone | int(11) | Maximum number of DNS slave zones |
| reseller_id | int(11) | ID of the reseller who owns this client |

## Relationships
- Related to `sys_user` table for login credentials
- Related to `server` table via various default server fields
- Related to `client_template` table via the `template_master` field
- May be self-referenced via the `parent_client_id` field for reseller relationships
- Referenced by various other tables like `web_domain`, `mail_domain`, etc.

## Notes
- Central table for client management in ISPConfig
- Contains comprehensive client information and contact details
- Manages resource limits and quotas for the client
- Controls which features are available to the client
- Supports reseller functionality through parent-child relationships
- The ISPConfig interface provides tools for creating and managing clients
