# dns_soa

## Description
This table stores DNS Start of Authority (SOA) records for zones managed by ISPConfig. SOA records define the authoritative information for a DNS zone, including primary nameserver, administrator email, and various timing parameters.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this zone |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the DNS server where this zone is hosted |
| origin | varchar(255) | Domain name of the zone (e.g., example.com) |
| ns | varchar(255) | Primary nameserver for the zone |
| mbox | varchar(255) | Email address of the zone administrator (in DNS format) |
| serial | int(11) | Zone serial number (incremented on changes) |
| refresh | int(11) | Refresh interval in seconds for secondary nameservers |
| retry | int(11) | Retry interval in seconds for failed zone transfers |
| expire | int(11) | Expiration time in seconds for secondary nameservers |
| minimum | int(11) | Minimum TTL in seconds for negative caching |
| ttl | int(11) | Default TTL in seconds for records in this zone |
| active | enum('n','y') | Whether this zone is active |
| xfer | varchar(255) | IP addresses allowed for zone transfers |
| also_notify | varchar(255) | Additional IP addresses to notify of zone changes |
| update_acl | varchar(255) | Access control list for dynamic updates |
| client_id | int(11) | ID of the client who owns this zone |
| zone_status | enum('OK','ERROR') | Current status of the zone |
| zone_status_reason | varchar(255) | Reason for the current status |
| zone_status_msg | text | Detailed status message |
| zone_status_updated | timestamp | Timestamp of the last status update |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `client` table via the `client_id` field
- Referenced by `dns_rr` table via the `zone` field

## Notes
- Defines the authoritative information for a DNS zone
- Each zone has exactly one SOA record
- Contains critical timing parameters for DNS propagation and caching
- The serial number is incremented automatically when changes are made to the zone
- The ISPConfig interface provides tools for creating and managing DNS zones
- Active flag can be used to temporarily disable zones without deleting them
- Zone status tracking helps identify and troubleshoot DNS configuration issues
