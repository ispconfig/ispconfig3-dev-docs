# ftp_traffic

## Description
This table stores FTP traffic usage statistics for websites hosted in ISPConfig. It tracks bandwidth consumption for FTP transfers on a monthly basis for monitoring and billing purposes.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| traffic_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this traffic record |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server where this traffic was measured |
| domain_id | int(11) | ID of the web domain (references web_domain) |
| traffic_date | date | Date of the traffic measurement (typically month start) |
| hostname | varchar(255) | Hostname of the website |
| traffic_bytes | bigint(32) | Traffic usage in bytes |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `web_domain` table via the `domain_id` field

## Notes
- Used for tracking FTP bandwidth usage of websites
- Important for enforcing traffic quotas and billing
- Traffic is typically measured and recorded monthly
- The ISPConfig control panel displays FTP traffic statistics based on this data
- May be used to generate reports or alerts when traffic limits are approached
- Similar in structure to other traffic tables like web_traffic
