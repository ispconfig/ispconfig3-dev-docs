# server

## Description
This table stores information about physical servers managed by ISPConfig.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| server_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this server record |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_name | varchar(255) | Name of the server |
| ip_address | varchar(255) | Main IP address of the server |
| ipv6_address | varchar(255) | Main IPv6 address of the server |
| hostname | varchar(255) | Hostname of the server |
| nameserver | varchar(255) | Primary nameserver |
| nameserver_ip | varchar(255) | IP address of the primary nameserver |
| firewall | varchar(1) | Whether firewall is enabled (Y/N) |
| active | varchar(1) | Whether the server is active (Y/N) |
| mirror_server_id | int(11) | ID of the mirror server if applicable |
| dbversion | int(11) | Database version running on the server |
| config | text | Server configuration in serialized format |
| updated | int(11) | Timestamp of last update |
| created | int(11) | Timestamp of creation |
| web_server | tinyint(1) | Whether this is a web server (1/0) |
| dns_server | tinyint(1) | Whether this is a DNS server (1/0) |
| file_server | tinyint(1) | Whether this is a file server (1/0) |
| db_server | tinyint(1) | Whether this is a database server (1/0) |
| vserver_server | tinyint(1) | Whether this is a virtualization server (1/0) |
| proxy_server | tinyint(1) | Whether this is a proxy server (1/0) |
| firewall_server | tinyint(1) | Whether this is a firewall server (1/0) |
| xmpp_server | tinyint(1) | Whether this is an XMPP server (1/0) |
| mail_server | tinyint(1) | Whether this is a mail server (1/0) |

## Relationships
- Related to `server_ip` table which stores additional IPs for this server
- Related to `server_ip_map` table which maps IPs to specific services
- Related to various service-specific tables that reference `server_id`
- May be referenced by `mirror_server_id` from other server records

## Notes
- Central table for server management in ISPConfig
- Defines server roles and capabilities through boolean flags
- Used for distributed setups where ISPConfig manages multiple servers
- Configuration details are typically stored in serialized format in the config field
