# Class: functions

Provides general utility functions for ISPConfig, including mail sending, IDN conversion, and various helpers. This class is loaded automatically by the ISPConfig framework.

**Source File:** interface/lib/classes/functions.inc.php

## Methods
- **mail($to, $subject, $text, $from, $filepath = '', $filetype = 'application/pdf', $filename = '', $cc = '', $bcc = '', $from_name = '')**
  - Sends an email via ISPConfig's mail subsystem, supporting attachments, CC/BCC, and SMTP configurations.
- **array_merge($array1, $array2)**
  - Merges two arrays; values in the second override those in the first.
- **currency_format($number, $view = '')**
  - Formats a number as currency, using locale-specific separators and decimal settings.
- **currency_unformat($number)**
  - Converts a formatted currency string back to a float.
- **get_ispconfig_url()**
  - Retrieves the base URL for the ISPConfig interface.
- **json_encode($data)**
  - Safely encodes data to JSON, with compatibility for older PHP versions.
- **suggest_ips($type = 'IPv4')**
  - Suggests available IPs for web, mail, or other services (IPv4/IPv6).
- **intval($value, $force_numeric = false)**
  - Returns the integer value of a variable, ensuring numeric safety.
- **formatBytes($size, $precision = 2)**
  - Converts bytes to human-readable units (kB, MB, GB, TB).
- **formatBytesOrUnlimited($size, $precision = 2)**
  - Converts bytes to human-readable units or returns 'Unlimited' for -1.
- **normalize_path($path)**
  - Normalizes file paths by removing duplicate slashes and resolving `..` segments.
- **idn_encode($domain)**
  - Encodes a UTF-8 domain to ASCII-compatible (punycode) using the IDN converter.
- **idn_decode($domain)**
  - Decodes a punycode domain back to UTF-8 using the IDN converter.
- **is_allowed_user($username, $restrict_names = false)**
  - Validates a username against allowed patterns; optional strict mode.
- **is_allowed_group($groupname, $restrict_names = false)**
  - Validates a group name against allowed patterns; optional strict mode.
- **getimagesizefromstring($string)**
  - Retrieves image dimensions from a binary string.
- **password($minLength = 10, $special = false)**
  - Generates a random password, optionally including special characters.
- **generate_customer_no()**
  - Generates a unique customer number based on existing records.
- **generate_ssh_key($client_id, $username = '')**
  - Generates an SSH key pair for the specified client and username.
- **htmlentities($value, $flags = ENT_COMPAT, $encoding = 'UTF-8', $double_encode = true)**
  - Converts characters to HTML entities with specified encoding and flags.
- **check_include_path($path)**
  - Validates an absolute include path to prevent directory traversal.
- **check_language($language)**
  - Ensures the provided language code is valid and falls back to default if needed.
- **func_client_lock($client_id, $locked)**
  - Locks or unlocks a client account, cascading status to child records.
- **func_client_cancel($client_id, $cancel)**
  - Disables or re-enables client accounts based on the cancel flag.
- **clientid_to_groups_list($client_id)**
  - Returns a comma-separated list of group IDs for a client and its sub-accounts.

## Properties
- **idn_converter**: Instance of the IDN converter.
- **idn_converter_name**: Name of the configured IDN converter.
