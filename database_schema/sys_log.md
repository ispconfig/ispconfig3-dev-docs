# sys_log

## Description
This table stores system log entries for the ISPConfig control panel. It records various events, actions, and errors that occur during system operation for auditing and troubleshooting purposes.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| syslog_id | int(11) | Primary key |
| server_id | int(11) | ID of the server where the event occurred |
| loglevel | enum('0','1','2') | Log level: 0 (debug), 1 (warning), 2 (error) |
| tstamp | int(11) | Unix timestamp when the event occurred |
| message | text | Log message content |
| datalog_id | int(11) | ID of the related datalog entry (if applicable) |
| source | varchar(255) | Source of the log entry (module, component, etc.) |

## Relationships
- Related to `server` table via the `server_id` field
- May be related to `sys_datalog` table via the `datalog_id` field

## Notes
- Used for tracking system events and errors
- Important for troubleshooting issues in the ISPConfig system
- Log entries can be filtered by log level, server, or source
- The ISPConfig interface provides a log viewer for administrators
- Regular maintenance may include purging old log entries to prevent excessive database growth
