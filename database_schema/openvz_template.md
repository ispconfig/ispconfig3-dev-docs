# openvz_template

## Description
This table stores OpenVZ template configurations used for creating virtual machines.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| template_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this template |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| template_name | varchar(255) | Name of the template |
| diskspace | int(11) | Disk space allocation in MB |
| traffic | int(11) | Traffic allocation |
| bandwidth | int(11) | Bandwidth limit |
| ram | int(11) | RAM allocation in MB |
| ram_burst | int(11) | RAM burst limit in MB |
| cpu_units | int(11) | CPU units allocation |
| cpu_num | int(11) | Number of CPUs |
| cpu_limit | int(11) | CPU usage limit in percent |
| io_priority | int(11) | I/O priority |
| active | varchar(255) | Whether the template is active (Y/N) |
| description | text | Description of the template |
| numproc | varchar(255) | Maximum number of processes |
| numtcpsock | varchar(255) | Maximum number of TCP sockets |
| numothersock | varchar(255) | Maximum number of other sockets |
| vmguarpages | varchar(255) | Guaranteed memory pages |
| kmemsize | varchar(255) | Kernel memory size |
| tcpsndbuf | varchar(255) | TCP send buffer size |
| tcprcvbuf | varchar(255) | TCP receive buffer size |
| othersockbuf | varchar(255) | Other socket buffer size |
| dgramrcvbuf | varchar(255) | Datagram receive buffer size |
| oomguarpages | varchar(255) | Out of memory guard pages |
| privvmpages | varchar(255) | Private VM pages |
| lockedpages | varchar(255) | Locked pages |
| shmpages | varchar(255) | Shared memory pages |
| physpages | varchar(255) | Physical pages |
| dcachesize | varchar(255) | Directory cache size |
| numfile | varchar(255) | Maximum number of files |
| numflock | varchar(255) | Maximum number of file locks |
| numpty | varchar(255) | Maximum number of pseudo terminals |
| numsiginfo | varchar(255) | Maximum number of siginfo structures |
| avnumproc | varchar(255) | Average number of processes |
| nameserver | varchar(255) | Nameserver IP address |
| create_date | datetime | Date when the template was created |

## Relationships
- Related to `openvz_vm` table where templates are applied to virtual machines

## Notes
- Templates define resource limits and configurations for OpenVZ containers
- Used by the OpenVZ virtualization system in ISPConfig
