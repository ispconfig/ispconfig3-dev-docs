# Class: sites_database_plugin

Handles database-related operations for websites in ISPConfig. Ensures database users and settings are synchronized with their parent website's configuration.

## Methods
- **processDatabaseInsert($form_page)**: Processes database insertions and updates settings to match the parent website.
- **processDatabaseUpdate($form_page)**: Updates database settings based on the parent website's configuration.
- **processDatabaseDelete($primary_id)**: Handles database deletions (currently empty implementation).

## Usage
This class is used by ISPConfig for managing database user and backup settings for websites.
