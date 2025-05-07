# help_faq_sections

## Description
This table stores sections for organizing frequently asked questions (FAQs) in the ISPConfig help system. It provides a hierarchical structure for categorizing FAQ entries.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(11) | Primary key |
| active | enum('n','y') | Whether this section is active |
| public | enum('n','y') | Whether this section is publicly visible |
| section_name | varchar(255) | Name of the section |
| order_id | int(11) | Order/position of this section in the list |

## Relationships
- Referenced by `help_faq` table via the `hf_section` field

## Notes
- Used for organizing FAQ entries into logical categories
- Provides structure to the help system in the ISPConfig control panel
- Active flag can be used to temporarily disable sections without deleting them
- Public flag controls whether the section is visible to all users or only administrators
- Order ID allows for custom sorting of sections in the help interface
- The ISPConfig interface provides tools for creating and managing FAQ sections
