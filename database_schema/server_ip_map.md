# server_ip_map

## Description
This table maps IP addresses to specific services on servers managed by ISPConfig, defining which services are bound to which IPs.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| server_ip_map_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this mapping |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server this mapping applies to |
| source_ip | varchar(255) | Source IP address |
| destination_ip | varchar(255) | Destination IP address (if applicable) |
| active | varchar(1) | Whether this mapping is active (Y/N) |
| source_port | int(11) | Source port number |
| destination_port | int(11) | Destination port number (if applicable) |
| service | varchar(255) | Service this mapping is for (e.g., 'web', 'dns', 'mail') |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `server_ip` table conceptually through the IP addresses

## Notes
- Used for configuring which services listen on which IP addresses
- Important for multi-IP setups where different services need different bindings
- Helps with security by limiting service exposure to specific interfaces
- May be used for port forwarding or service redirection in some cases
