# dns_rr

## Description
This table stores DNS resource records (RR) for zones managed by ISPConfig. It contains individual DNS records like A, AAAA, MX, CNAME, TXT, etc., that define the DNS configuration for domains.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this record |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the DNS server where this record is hosted |
| zone | int(11) | ID of the DNS zone (references dns_soa) |
| name | varchar(255) | Name/hostname part of the record |
| type | varchar(16) | Record type (A, AAAA, MX, CNAME, TXT, etc.) |
| data | varchar(255) | Record data (e.g., IP address for A records) |
| aux | int(11) | Auxiliary data (e.g., priority for MX records) |
| ttl | int(11) | Time to live in seconds |
| active | enum('n','y') | Whether this record is active |
| stamp | timestamp | Timestamp of the last update |
| serial | int(11) | Zone serial number when this record was last updated |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `dns_soa` table via the `zone` field

## Notes
- Contains individual DNS records for domains
- Supports all standard DNS record types
- Each record belongs to a specific DNS zone (SOA record)
- The ISPConfig interface provides tools for creating and managing DNS records
- Active flag can be used to temporarily disable records without deleting them
- Serial number tracking helps with zone transfers and updates
- Critical for proper domain name resolution and email delivery
