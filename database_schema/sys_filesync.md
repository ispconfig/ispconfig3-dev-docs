# sys_filesync

## Description
This table stores information about file synchronization between the primary ISPConfig server and secondary servers in a multi-server setup. It tracks which files need to be synchronized across servers.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(11) | Primary key |
| server_id | int(11) | ID of the server this synchronization applies to |
| session_id | varchar(64) | Session ID associated with the synchronization |
| file | varchar(255) | Path to the file that needs to be synchronized |
| action | varchar(10) | Action to perform: 'insert', 'update', or 'delete' |
| status | varchar(10) | Status of the synchronization: 'pending', 'ok', or 'error' |
| tstamp | int(11) | Unix timestamp when the synchronization was requested |
| error | text | Error message if synchronization failed |

## Relationships
- Related to `server` table via the `server_id` field

## Notes
- Used in multi-server setups to keep files synchronized across servers
- Part of the distributed architecture of ISPConfig
- Typically handles configuration files for services like web servers, mail servers, etc.
- The ISPConfig server daemon processes these entries to apply file changes to secondary servers
- Critical for maintaining consistent configuration across a cluster of servers
