# sys_theme

## Description
This table stores information about visual themes available in the ISPConfig control panel. Themes control the appearance and styling of the user interface.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| theme_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this theme |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| name | varchar(64) | Name of the theme |
| description | text | Description of the theme |
| css_file | varchar(255) | Path to the CSS file for this theme |
| logo_file | varchar(255) | Path to the logo file for this theme |
| favicon_file | varchar(255) | Path to the favicon file for this theme |
| background_image | varchar(255) | Path to the background image for this theme |
| background_color | varchar(7) | Background color in hex format (e.g., #FFFFFF) |
| text_color | varchar(7) | Text color in hex format |
| link_color | varchar(7) | Link color in hex format |
| active | tinyint(1) | Whether this theme is active (1) or not (0) |

## Relationships
- May be referenced by `sys_user` table for user theme preferences
- May be referenced by `sys_session` table for session theme settings

## Notes
- Used for customizing the appearance of the ISPConfig control panel
- Allows for branding and visual customization
- Users can select their preferred theme in their profile settings
- Administrators can create and manage themes for all users
- Default themes are typically included with the ISPConfig installation
