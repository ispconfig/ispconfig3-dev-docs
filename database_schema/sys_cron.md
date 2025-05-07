# sys_cron

## Description
This table stores information about scheduled tasks (cron jobs) that are executed by the ISPConfig system at regular intervals.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this cron job |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server this cron job runs on (0 for all servers) |
| run_min | varchar(255) | Minute field of cron expression (0-59, * for all) |
| run_hour | varchar(255) | Hour field of cron expression (0-23, * for all) |
| run_mday | varchar(255) | Day of month field of cron expression (1-31, * for all) |
| run_month | varchar(255) | Month field of cron expression (1-12, * for all) |
| run_wday | varchar(255) | Day of week field of cron expression (0-7, * for all) |
| command | text | Command or script to execute |
| last_run | datetime | Timestamp of the last execution |
| next_run | datetime | Timestamp of the next scheduled execution |
| active | enum('n','y') | Whether this cron job is active |
| parent_domain_id | int(11) | Parent domain ID (if applicable) |
| type | varchar(255) | Type of cron job (system, user, etc.) |

## Relationships
- Related to `server` table via the `server_id` field
- May be related to `web_domain` table via the `parent_domain_id` field

## Notes
- Used for scheduling recurring tasks in the ISPConfig system
- System cron jobs handle maintenance tasks like backups, log rotation, etc.
- User cron jobs may be created by clients for their own websites
- The ISPConfig server daemon checks this table to determine which tasks to run
- Follows standard cron expression format for scheduling
