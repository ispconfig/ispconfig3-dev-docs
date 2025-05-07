# dns_template

## Description
This table stores templates for DNS zones in ISPConfig. These templates define default DNS records and settings that can be applied when creating new DNS zones.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| template_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this template |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| name | varchar(64) | Name of the template |
| fields | text | Template fields in serialized format |
| template | text | Template content in serialized format |
| visible | enum('N','Y') | Whether this template is visible in the interface |

## Relationships
- May be used when creating new DNS zones in the `dns_soa` table

## Notes
- Used for standardizing DNS zone creation
- Templates can include default records like MX, A, AAAA, CNAME, etc.
- Simplifies the process of creating new DNS zones with consistent settings
- The ISPConfig interface provides tools for creating and managing DNS templates
- Visibility flag controls whether the template appears in the interface
- Particularly useful for hosting providers who need to create many similar DNS zones
