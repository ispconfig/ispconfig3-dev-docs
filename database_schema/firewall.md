# firewall

## Description
This table stores firewall rules for servers managed by ISPConfig. It contains configuration for the server firewall, including rules for allowing or blocking specific traffic.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| firewall_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this firewall rule |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server where this firewall rule applies |
| active | enum('n','y') | Whether this firewall rule is active |
| tcp_port | varchar(255) | TCP ports affected by this rule |
| udp_port | varchar(255) | UDP ports affected by this rule |
| protocol | varchar(255) | Protocol for this rule (tcp, udp, both) |
| source_ip | varchar(255) | Source IP address or network |
| destination_ip | varchar(255) | Destination IP address or network |
| action | varchar(255) | Action to take (ACCEPT, DROP, REJECT) |
| state | varchar(255) | Connection state for this rule |
| target | varchar(255) | Target for this rule (e.g., ACCEPT, DROP) |
| direction | varchar(255) | Direction of traffic (in, out) |

## Relationships
- Related to `server` table via the `server_id` field

## Notes
- Used for configuring firewall rules on servers
- Controls network access to and from the server
- Rules can be based on ports, protocols, IP addresses, and connection states
- The ISPConfig interface provides tools for creating and managing firewall rules
- Active flag can be used to temporarily disable rules without deleting them
- Important for server security and access control
- Typically implemented using iptables or similar firewall systems
