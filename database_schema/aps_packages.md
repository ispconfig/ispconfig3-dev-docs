# aps_packages

## Description
This table stores information about available APS (Application Packaging Standard) packages in ISPConfig. It contains metadata about applications that can be installed through the APS installer.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(4) | Primary key |
| path | varchar(255) | Path to the APS package files |
| name | varchar(255) | Name of the application |
| category | varchar(255) | Category of the application |
| version | varchar(255) | Version of the application |
| release | int(4) | Release number |
| package_version | varchar(255) | Version of the APS package format |
| vendor | varchar(255) | Vendor or developer of the application |
| serverid | varchar(255) | ID of the server where the package is available |
| package_url | text | URL to download the package |
| package_status | int(1) | Status of the package (e.g., available, deprecated) |
| package_status_detail | text | Detailed status information |
| package_status_changed | datetime | Timestamp when the status last changed |
| package_installable | int(1) | Whether the package can be installed (1) or not (0) |
| package_requires_db | varchar(255) | Database requirements for the package |
| package_conflict | text | Conflicts with other packages |
| package_requirements | text | System requirements in serialized format |
| package_md5 | varchar(255) | MD5 checksum of the package |
| package_icon | varchar(255) | Path to the package icon |
| package_description | mediumtext | Description of the application |
| package_dep | text | Dependencies in serialized format |
| package_dep_install | text | Installation dependencies in serialized format |
| package_dep_conflict | text | Conflicting dependencies in serialized format |
| package_dep_recommendation | text | Recommended dependencies in serialized format |
| package_settings | text | Default settings in serialized format |
| package_type | varchar(255) | Type of package (e.g., web application, service) |
| package_is_visible | int(1) | Whether the package is visible in the interface (1) or not (0) |
| package_is_core | int(1) | Whether the package is a core component (1) or not (0) |
| package_is_installable | int(1) | Whether the package can be installed (1) or not (0) |

## Relationships
- Referenced by `aps_instances` table via the `package_id` field
- May be related to `aps_settings` table for global APS settings

## Notes
- Used for managing available APS applications in the ISPConfig system
- APS is a standard for packaging and deploying web applications
- Contains comprehensive metadata about applications for the installer interface
- Tracks compatibility requirements and dependencies
- The ISPConfig interface uses this information to display available applications
- Part of the app installer functionality in ISPConfig
