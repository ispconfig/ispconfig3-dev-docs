# openvz_ip

## Description
This table stores information about IP addresses assigned to OpenVZ virtual containers in ISPConfig. It manages the allocation and tracking of IP addresses for virtualization.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| ip_address_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this IP address |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server where this IP address is configured |
| ip_address | varchar(255) | The IP address |
| vm_id | int(11) | ID of the virtual machine this IP is assigned to (references openvz_vm) |
| additional_ip | enum('n','y') | Whether this is an additional IP for the VM |
| active | enum('n','y') | Whether this IP address is active |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `openvz_vm` table via the `vm_id` field

## Notes
- Used for managing IP addresses for OpenVZ virtual containers
- Tracks which virtual machine is using each IP address
- Supports both primary and additional IPs for virtual machines
- The ISPConfig interface provides tools for assigning and managing IP addresses
- Active flag can be used to temporarily disable IP addresses without removing them
- Part of the virtualization management functionality in ISPConfig
- OpenVZ is a container-based virtualization technology for Linux
