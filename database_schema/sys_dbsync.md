# sys_dbsync

## Description
This table stores information about database synchronization between the primary ISPConfig server and secondary servers in a multi-server setup. It tracks which database changes have been synchronized to which servers.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(11) | Primary key |
| jobname | varchar(64) | Name of the synchronization job |
| sync_interval_minutes | int(11) | Interval in minutes between synchronization runs |
| db_type | varchar(16) | Type of database (typically 'mysql') |
| db_host | varchar(255) | Database host to connect to |
| db_name | varchar(64) | Database name to synchronize |
| db_username | varchar(64) | Username for database connection |
| db_password | varchar(64) | Password for database connection (encrypted) |
| db_tables | text | List of tables to synchronize |
| db_sql_query | text | Custom SQL query for synchronization (if applicable) |
| sync_field_name | varchar(255) | Field name used to track synchronization status |
| server_id | int(11) | ID of the server this synchronization applies to |
| last_exec | bigint(20) | Timestamp of the last execution |
| active | enum('n','y') | Whether this synchronization job is active |

## Relationships
- Related to `server` table via the `server_id` field

## Notes
- Used in multi-server setups to keep database content synchronized
- Part of the distributed architecture of ISPConfig
- Allows for selective synchronization of specific tables
- Can be configured with custom SQL queries for complex synchronization scenarios
- Typically runs at regular intervals as defined by the sync_interval_minutes field
