# openvz_vm

## Description
This table stores information about OpenVZ virtual machines managed by ISPConfig.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| vm_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this VM |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the physical server hosting this VM |
| vserver_id | int(11) | OpenVZ container ID (CTID) |
| ostemplate_id | int(11) | ID of the OS template used (references openvz_ostemplate) |
| template_id | int(11) | ID of the resource template used (references openvz_template) |
| ip_address | varchar(255) | Primary IP address of the VM |
| hostname | varchar(255) | Hostname of the VM |
| vm_password | varchar(255) | Root password (encrypted) |
| start_boot | varchar(1) | Whether to start VM on boot (Y/N) |
| active | varchar(1) | Whether the VM is active (Y/N) |
| active_until_date | date | Date until which the VM is active |
| description | text | Description of the VM |
| diskspace | int(11) | Disk space allocation in MB |
| traffic | int(11) | Traffic allocation |
| bandwidth | int(11) | Bandwidth limit |
| ram | int(11) | RAM allocation in MB |
| ram_burst | int(11) | RAM burst limit in MB |
| cpu_units | int(11) | CPU units allocation |
| cpu_num | int(11) | Number of CPUs |
| cpu_limit | int(11) | CPU usage limit in percent |
| io_priority | int(11) | I/O priority |
| nameserver | varchar(255) | Nameserver IP address |
| create_date | datetime | Date when the VM was created |
| status | varchar(255) | Current status of the VM |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `openvz_ostemplate` table via the `ostemplate_id` field
- Related to `openvz_template` table via the `template_id` field
- Related to `openvz_traffic` table which tracks traffic for this VM
- Related to `openvz_ip` table which may store additional IPs for this VM

## Notes
- Central table for OpenVZ virtualization management in ISPConfig
- Stores both configuration parameters and runtime information
- Used for creating, managing, and monitoring OpenVZ containers
