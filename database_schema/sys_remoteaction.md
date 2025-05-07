# sys_remoteaction

## Description
This table stores information about remote actions that need to be executed on servers managed by ISPConfig. It's part of the distributed architecture that allows the control panel to manage multiple servers.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| action_id | int(11) | Primary key |
| server_id | int(11) | ID of the server where the action should be executed |
| tstamp | int(11) | Unix timestamp when the action was created |
| action_type | varchar(20) | Type of action to be performed |
| action_param | mediumtext | Parameters for the action in serialized format |
| status | enum('pending','ok','error') | Current status of the action |
| error | mediumtext | Error message if the action failed |
| source_server_id | int(11) | ID of the server that initiated the action |

## Relationships
- Related to `server` table via the `server_id` field (target server)
- Related to `server` table via the `source_server_id` field (source server)

## Notes
- Used for executing commands or scripts on remote servers
- Part of the distributed architecture of ISPConfig
- The ISPConfig server daemon processes these entries to execute actions on remote servers
- Typical actions include service restarts, configuration updates, or maintenance tasks
- Status field tracks whether the action is pending, completed successfully, or failed
- Error field provides diagnostic information if the action fails
