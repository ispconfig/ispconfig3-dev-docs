# cron

## Description
This table stores information about cron jobs (scheduled tasks) for websites hosted in ISPConfig. It allows clients to set up scheduled tasks for their websites.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this cron job |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server where this cron job runs |
| parent_domain_id | int(11) | ID of the parent web domain (references web_domain) |
| type | varchar(8) | Type of cron job (e.g., 'url', 'chrooted', 'full') |
| command | text | Command or URL to execute |
| run_min | varchar(100) | Minute field of cron expression (0-59, * for all) |
| run_hour | varchar(100) | Hour field of cron expression (0-23, * for all) |
| run_mday | varchar(100) | Day of month field of cron expression (1-31, * for all) |
| run_month | varchar(100) | Month field of cron expression (1-12, * for all) |
| run_wday | varchar(100) | Day of week field of cron expression (0-7, * for all) |
| active | enum('n','y') | Whether this cron job is active |
| log | enum('n','y') | Whether to log the cron job execution |
| log_output | text | Output from the last execution |
| last_run | datetime | Timestamp of the last execution |
| next_run | datetime | Timestamp of the next scheduled execution |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `web_domain` table via the `parent_domain_id` field

## Notes
- Used for scheduling recurring tasks for websites
- Supports different types of cron jobs:
  - 'url' for accessing a URL at scheduled times
  - 'chrooted' for running commands in a chrooted environment
  - 'full' for running commands with full system access
- Follows standard cron expression format for scheduling
- The ISPConfig interface provides tools for creating and managing cron jobs
- Log option allows for tracking the output and success of cron job executions
