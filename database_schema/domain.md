# domain

## Description
This table stores information about domains registered in the ISPConfig system. It tracks domain registrations, expiration dates, and related metadata.

## Table Schema
| Column | Type | Description |
|--------|------|-------------|
| domain_id | int(11) | Primary key |
| sys_userid | int(11) | System user ID who owns this domain |
| sys_groupid | int(11) | System group ID |
| sys_perm_user | varchar(5) | User permissions |
| sys_perm_group | varchar(5) | Group permissions |
| sys_perm_other | varchar(5) | Other permissions |
| domain | varchar(255) | Domain name (e.g., example.com) |
| registrar | varchar(255) | Domain registrar name |
| registration_date | date | Date when the domain was registered |
| expiration_date | date | Date when the domain registration expires |
| client_id | int(11) | ID of the client who owns this domain |
| dns_ns1 | varchar(255) | Primary nameserver |
| dns_ns2 | varchar(255) | Secondary nameserver |
| dns_ns3 | varchar(255) | Tertiary nameserver |
| dns_ns4 | varchar(255) | Quaternary nameserver |
| dns_ns5 | varchar(255) | Quinary nameserver |
| dns_ns6 | varchar(255) | Senary nameserver |
| dns_ns7 | varchar(255) | Septenary nameserver |
| dns_ns8 | varchar(255) | Octonary nameserver |
| dns_ns9 | varchar(255) | Nonary nameserver |
| dns_ns10 | varchar(255) | Denary nameserver |
| dns_adminc | varchar(255) | Administrative contact |
| dns_techc | varchar(255) | Technical contact |
| dns_billc | varchar(255) | Billing contact |
| dns_zonec | varchar(255) | Zone contact |
| tld | varchar(255) | Top-level domain (e.g., com, org, net) |
| locked | enum('n','y') | Whether the domain is locked for transfers |
| status | varchar(255) | Current status of the domain |
| added_date | date | Date when the domain was added to the system |
| added_by | varchar(255) | User who added the domain |

## Relationships
- Related to `client` table via the `client_id` field
- May be related to `dns_soa` table conceptually through the domain name

## Notes
- Used for tracking domain registrations and expiration dates
- Contains nameserver information for the domain
- Includes contact information for domain administration
- The ISPConfig interface provides tools for managing domain registrations
- Locked flag can prevent accidental domain transfers
- Important for domain renewal reminders and management
- Different from web_domain table which focuses on website hosting
