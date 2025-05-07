# aps_settings

## Description
This table stores global settings for the APS (Application Packaging Standard) installer system in ISPConfig. It contains configuration parameters that control the behavior of the APS installer.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(4) | Primary key |
| name | varchar(255) | Name of the setting |
| value | text | Value of the setting |
| status | int(4) | Status of the setting |

## Relationships
- Conceptually related to `aps_packages` and `aps_instances` tables

## Notes
- Used for storing global configuration settings for the APS installer
- Each record represents a single global setting for the APS system
- Settings can include repository URLs, update intervals, security parameters, etc.
- The name-value pair format allows for flexible configuration storage
- Settings are typically managed through the ISPConfig admin interface
- Critical for proper functioning of the APS installer system
