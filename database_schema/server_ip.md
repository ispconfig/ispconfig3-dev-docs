# server_ip

## Description
This table stores information about IP addresses associated with servers managed by ISPConfig.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| server_ip_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this IP record |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server this IP belongs to |
| client_id | int(11) | ID of the client this IP is assigned to (if applicable) |
| ip_type | varchar(255) | Type of IP (IPv4 or IPv6) |
| ip_address | varchar(255) | The IP address |
| virtualhost | varchar(255) | Whether this IP is used for virtual hosting |
| virtualhost_port | varchar(255) | Port used for virtual hosting |
| active | varchar(1) | Whether the IP is active (Y/N) |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `client` table via the `client_id` field
- Related to `server_ip_map` table which maps IPs to specific services

## Notes
- Used for managing multiple IP addresses assigned to servers
- Important for web hosting with dedicated IPs per site
- Allows tracking which IPs are assigned to which clients
- Used by various services that need to bind to specific IPs
