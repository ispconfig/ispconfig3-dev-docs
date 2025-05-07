# dns_slave

## Description
This table stores information about slave DNS zones in ISPConfig. Slave zones are secondary copies of DNS zones that are maintained through zone transfers from a master DNS server.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this slave zone |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the DNS server where this slave zone is hosted |
| origin | varchar(255) | Domain name of the slave zone (e.g., example.com) |
| ns | varchar(255) | Nameserver for the slave zone |
| active | enum('n','y') | Whether this slave zone is active |
| xfer | varchar(255) | IP addresses allowed for zone transfers |
| client_id | int(11) | ID of the client who owns this slave zone |
| source | varchar(255) | IP address of the master DNS server |
| zone_status | enum('OK','ERROR') | Current status of the slave zone |
| zone_status_reason | varchar(255) | Reason for the current status |
| zone_status_msg | text | Detailed status message |
| zone_status_updated | timestamp | Timestamp of the last status update |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `client` table via the `client_id` field

## Notes
- Used for configuring secondary (slave) DNS zones
- Slave zones receive updates through zone transfers from a master server
- Provides DNS redundancy and improved performance through distributed nameservers
- The source field specifies the master DNS server's IP address
- The ISPConfig interface provides tools for creating and managing slave zones
- Active flag can be used to temporarily disable slave zones without deleting them
- Zone status tracking helps identify and troubleshoot zone transfer issues
