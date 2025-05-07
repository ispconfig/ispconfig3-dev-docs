# sys_session

## Description
This table stores session information for users logged into the ISPConfig control panel. It maintains the state of user sessions and authentication data.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| session_id | varchar(64) | Primary key - unique session identifier |
| username | varchar(255) | Username of the logged-in user |
| ip | varchar(39) | IP address of the client |
| login | int(11) | Unix timestamp of when the session was created |
| lastlogin | int(11) | Unix timestamp of the last activity in this session |
| formkey | varchar(64) | Security key for form submissions to prevent CSRF attacks |
| client_id | int(11) | ID of the client this user belongs to (if applicable) |
| theme | varchar(64) | Theme selected for this session |
| language | varchar(2) | Language code for the user interface |
| remote_functions | text | List of remote functions this session is allowed to execute |
| remote_session | varchar(64) | ID of the remote session (if applicable) |
| user_id | int(11) | ID of the user in the sys_user table |

## Relationships
- Related to `sys_user` table via the `user_id` field
- Related to `client` table via the `client_id` field
- May be related to `remote_session` table conceptually

## Notes
- Used for tracking user sessions in the ISPConfig control panel
- Sessions typically expire after a period of inactivity
- Contains security information like the formkey to prevent CSRF attacks
- Stores user preferences like theme and language
- The ISPConfig system periodically cleans up expired sessions
