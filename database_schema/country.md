# country

## Description
This table stores information about countries for use throughout the ISPConfig system. It contains country names, codes, and other relevant data for address and location management.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| iso | char(2) | Primary key - ISO 3166-1 alpha-2 country code |
| name | varchar(64) | Country name |
| printable_name | varchar(64) | Printable/display name of the country |
| iso3 | char(3) | ISO 3166-1 alpha-3 country code |
| numcode | smallint(6) | ISO 3166-1 numeric country code |
| eu | tinyint(1) | Whether the country is in the European Union (1) or not (0) |
| special | tinyint(1) | Whether this is a special entry (1) or a standard country (0) |
| iso_register | varchar(255) | ISO registration information |

## Relationships
- May be referenced by `client` table for client addresses
- May be used by various address-related functions throughout the system

## Notes
- Used as a reference table for country selection in forms
- Contains standardized country codes for international compatibility
- EU flag is useful for handling EU-specific requirements (e.g., VAT rules)
- The special flag may indicate non-standard entries like territories or regions
- This is primarily a static reference table that rarely changes
