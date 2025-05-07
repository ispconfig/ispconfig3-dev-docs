# webdav_user

## Description
This table stores information about WebDAV users who have access to websites hosted in ISPConfig. It tracks usernames, passwords, and access permissions for WebDAV protocol access.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| webdav_user_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this WebDAV user |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| server_id | int(11) | ID of the server where this WebDAV user exists |
| parent_domain_id | int(11) | ID of the parent web domain (references web_domain) |
| username | varchar(255) | Username for WebDAV access |
| password | varchar(255) | Encrypted password for WebDAV access |
| dir | varchar(255) | Directory path this user has access to |
| active | enum('n','y') | Whether this WebDAV user is active |

## Relationships
- Related to `server` table via the `server_id` field
- Related to `web_domain` table via the `parent_domain_id` field

## Notes
- Used for managing WebDAV access to websites
- WebDAV (Web Distributed Authoring and Versioning) allows remote file management over HTTP
- Enables users to mount website directories as network drives
- Useful for content management and file uploads
- The ISPConfig interface provides tools for creating and managing WebDAV users
- Directory path is typically relative to the web domain's document root
