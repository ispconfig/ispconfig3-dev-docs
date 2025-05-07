# openvz_traffic

## Description
This table stores traffic usage statistics for OpenVZ virtual machines.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| traffic_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this record |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| vserver_id | int(11) | ID of the virtual server (references openvz_vm) |
| traffic_date | date | Date of the traffic measurement |
| traffic_bytes | bigint(32) | Traffic usage in bytes |
| hostname | varchar(255) | Hostname of the virtual server |

## Relationships
- Related to `openvz_vm` table via the `vserver_id` field

## Notes
- Used for tracking and billing traffic usage of OpenVZ containers
- Traffic is typically measured daily for each virtual server
- Part of the OpenVZ virtualization monitoring system in ISPConfig
