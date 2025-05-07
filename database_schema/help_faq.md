# help_faq

## Description
This table stores frequently asked questions (FAQs) and their answers for the ISPConfig help system. It contains the content of the FAQ entries displayed in the control panel.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| id | int(11) | Primary key |
| hf_section | int(11) | ID of the FAQ section (references help_faq_sections) |
| active | enum('n','y') | Whether this FAQ entry is active |
| public | enum('n','y') | Whether this FAQ entry is publicly visible |
| question | text | The question text |
| answer | text | The answer text |
| order_id | int(11) | Order/position of this FAQ entry within its section |

## Relationships
- Related to `help_faq_sections` table via the `hf_section` field

## Notes
- Used for providing help and documentation within the ISPConfig control panel
- FAQ entries are organized into sections for easier navigation
- Active flag can be used to temporarily disable entries without deleting them
- Public flag controls whether the entry is visible to all users or only administrators
- Order ID allows for custom sorting of FAQ entries within a section
- The ISPConfig interface provides tools for creating and managing FAQ entries
