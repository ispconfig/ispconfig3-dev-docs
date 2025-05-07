# aps_instances_settings

## Description
This table stores configuration settings for installed APS (Application Packaging Standard) application instances in ISPConfig. It contains the specific settings and parameters for each APS application installation.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(4) | Primary key |
| instance_id | int(4) | ID of the APS instance (references aps_instances) |
| name | varchar(255) | Name of the setting |
| value | mediumtext | Value of the setting |
| status | int(4) | Status of the setting |

## Relationships
- Related to `aps_instances` table via the `instance_id` field

## Notes
- Used for storing configuration settings for APS application instances
- Each record represents a single setting for a specific APS instance
- Settings can include database connection details, application parameters, etc.
- The name-value pair format allows for flexible configuration storage
- Settings are typically managed through the APS installer interface
- Critical for proper functioning of installed APS applications
