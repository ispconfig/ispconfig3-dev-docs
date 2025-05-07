# sys_datalog

## Description
This table stores a log of changes made to data in the ISPConfig system. It records modifications to records in various tables, enabling auditing, synchronization, and potential rollback of changes.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| datalog_id | int(11) | Primary key |
| server_id | int(11) | ID of the server where the change occurred |
| dbtable | varchar(255) | Name of the database table that was modified |
| dbidx | varchar(255) | Primary key field name of the affected table |
| action | char(1) | Type of action: 'i' (insert), 'u' (update), 'd' (delete) |
| tstamp | int(11) | Unix timestamp when the change occurred |
| user | varchar(255) | Username of the user who made the change |
| data | longtext | Serialized data representing the change |
| status | set('pending','ok','error') | Status of the datalog entry processing |
| error | text | Error message if processing failed |
| session_id | varchar(64) | Session ID associated with the change |
| dbidx_value | varchar(255) | Value of the primary key for the affected record |

## Relationships
- Related to `server` table via the `server_id` field
- Related to various other tables through the `dbtable` and `dbidx_value` fields

## Notes
- Critical for the distributed architecture of ISPConfig
- Used by the server synchronization system to propagate changes across multiple servers
- Enables auditing of changes made to the system
- Helps with debugging and troubleshooting
- The ISPConfig server daemon processes these entries to apply changes to the actual server configuration
