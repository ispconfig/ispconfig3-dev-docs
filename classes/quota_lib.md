# Class: quota_lib

Provides methods for retrieving and calculating disk quota usage for client websites in ISPConfig. Aggregates quota data from monitoring records and correlates it with user websites.

## Methods
- **get_quota_data($clientid = null, $readable = true)**
  - Retrieves quota usage data for all or a specific client's websites. Returns usage, limits, and file counts, and formats results for display. Also calculates usage percentages and assigns display colors based on quota status.

## Usage
This class is used internally by ISPConfig to display and process disk quota information for client websites, supporting both raw and human-readable outputs.
