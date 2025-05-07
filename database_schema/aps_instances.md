# aps_instances

## Description
This table stores information about installed APS (Application Packaging Standard) application instances in ISPConfig. It tracks which APS packages have been installed for which clients.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(4) | Primary key |
| sys_userid | int(11) | System user ID who owns this instance |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| package_id | int(4) | ID of the APS package (references aps_packages) |
| customer_id | int(4) | ID of the customer who owns this instance |
| instance_status | int(4) | Status of the instance (e.g., installed, failed, pending) |
| instance_status_detail | mediumtext | Detailed status information |
| instance_status_error | mediumtext | Error message if installation failed |
| instance_status_changed | datetime | Timestamp when the status last changed |
| instance_date | datetime | Timestamp when the instance was created |
| domain | varchar(255) | Domain where the application is installed |
| admin_password | varchar(255) | Admin password for the application (encrypted) |
| saas_settings | text | Software as a Service settings in serialized format |

## Relationships
- Related to `aps_packages` table via the `package_id` field
- Related to `client` table via the `customer_id` field
- Related to `aps_instances_settings` table which contains additional settings

## Notes
- Used for tracking installed APS applications in the ISPConfig system
- APS is a standard for packaging and deploying web applications
- Instances represent individual installations of APS packages
- Status tracking allows for monitoring installation progress or failures
- The ISPConfig interface provides tools for installing and managing APS applications
- Part of the app installer functionality in ISPConfig
