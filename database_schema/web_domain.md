# web_domain

## Description
This table stores information about web domains (websites) hosted in ISPConfig. It is one of the central tables in the system, containing configuration details for websites, including paths, server settings, and various options.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| domain_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this domain |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server where this domain is hosted |
| ip_address | varchar(39) | Primary IP address for this domain |
| ipv6_address | varchar(255) | IPv6 address for this domain (if applicable) |
| domain | varchar(255) | Domain name (e.g., example.com) |
| type | varchar(32) | Type of domain (e.g., 'vhost', 'alias') |
| parent_domain_id | int(11) | ID of the parent domain (for subdomains or aliases) |
| vhost_type | varchar(32) | Virtual host type (e.g., 'name', 'ip') |
| hd_quota | bigint(20) | Disk quota in bytes |
| traffic_quota | bigint(20) | Traffic quota in bytes |
| cgi | enum('n','y') | Whether CGI is enabled |
| ssi | enum('n','y') | Whether SSI is enabled |
| suexec | enum('n','y') | Whether suEXEC is enabled |
| php | enum('n','y','fast-cgi','cgi','mod','php-fpm') | PHP execution mode |
| ruby | enum('n','y') | Whether Ruby is enabled |
| python | enum('n','y') | Whether Python is enabled |
| active | enum('n','y') | Whether this domain is active |
| document_root | varchar(255) | Path to the document root directory |
| system_user | varchar(255) | System user that owns the files |
| system_group | varchar(255) | System group that owns the files |
| php_open_basedir | mediumtext | PHP open_basedir setting |
| custom_php_ini | mediumtext | Custom PHP configuration |
| backup_interval | varchar(255) | Backup interval for this domain |
| backup_copies | int(11) | Number of backup copies to keep |
| ssl | enum('n','y') | Whether SSL is enabled |
| ssl_letsencrypt | enum('n','y') | Whether Let's Encrypt SSL is used |
| ssl_cert | mediumtext | SSL certificate content |
| ssl_key | mediumtext | SSL private key content |
| ssl_bundle | mediumtext | SSL certificate bundle content |
| ssl_action | varchar(16) | Action for SSL (e.g., 'create', 'renew') |
| stats_password | varchar(255) | Password for statistics access |
| stats_type | varchar(255) | Type of statistics (e.g., 'awstats', 'webalizer') |
| allow_override | varchar(255) | Apache AllowOverride setting |
| apache_directives | mediumtext | Custom Apache directives |
| nginx_directives | mediumtext | Custom Nginx directives |
| php_fpm_use_socket | enum('n','y') | Whether to use PHP-FPM socket |
| pm | varchar(255) | PHP-FPM process manager (e.g., 'dynamic', 'static') |
| pm_max_children | int(11) | PHP-FPM max children setting |
| pm_start_servers | int(11) | PHP-FPM start servers setting |
| pm_min_spare_servers | int(11) | PHP-FPM min spare servers setting |
| pm_max_spare_servers | int(11) | PHP-FPM max spare servers setting |
| pm_process_idle_timeout | int(11) | PHP-FPM process idle timeout |
| pm_max_requests | int(11) | PHP-FPM max requests setting |
| rewrite_rules | mediumtext | URL rewrite rules |
| added_date | date | Date when the domain was added |
| added_by | varchar(255) | User who added the domain |
| http_port | int(11) | HTTP port (typically 80) |
| https_port | int(11) | HTTPS port (typically 443) |
| subdomain | enum('none','www','*') | Subdomain handling |
| php_values | mediumtext | Custom PHP values |
| client_id | int(11) | ID of the client who owns this domain |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `client` table via the `client_id` field
- Self-referenced via the `parent_domain_id` field for subdomains/aliases
- Referenced by `web_database` table via the `parent_domain_id` field
- Referenced by `web_folder` table via the `parent_domain_id` field
- Referenced by `web_backup` table via the `parent_domain_id` field

## Notes
- Central table for website management in ISPConfig
- Contains comprehensive configuration for web hosting
- Supports various web server configurations (Apache, Nginx)
- Handles SSL certificate management including Let's Encrypt
- Controls PHP execution modes and settings
- Manages resource quotas and limits
- Supports custom directives for fine-grained control
- The ISPConfig interface provides tools for creating and managing websites
