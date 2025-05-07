# remote_session

## Description
This table stores information about remote sessions established to manage ISPConfig servers.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| session_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who initiated the session |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| remote_userid | int(11) | ID of the remote user (references remote_user) |
| remote_functions | text | List of functions allowed in this session |
| tstamp | int(10) | Timestamp when the session was created |
| remote_ip | varchar(255) | IP address of the remote connection |
| remote_port | int(11) | Port of the remote connection |
| server_id | int(11) | ID of the server being accessed |
| session_state | varchar(255) | Current state of the session |

## Relationships
- Related to `remote_user` table via the `remote_userid` field
- Related to `server` table via the `server_id` field

## Notes
- Used for tracking and managing remote access sessions to ISPConfig servers
- Part of the security and access control system in ISPConfig
- Sessions may have limited access to specific functions based on permissions
