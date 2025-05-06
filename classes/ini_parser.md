# Class: ini_parser

Provides methods for parsing INI-formatted strings into associative arrays and converting arrays back to INI strings. Used throughout ISPConfig for reading and writing configuration data.

**Source File:** interface/lib/classes/ini_parser.inc.php

## Methods
- **parse_ini_string($ini)**
  - Parses an INI-formatted string (supports sections and key=value pairs) into an associative array and caches it.
- **get_ini_string($config_array = '')**
  - Converts an associative array (optionally provided) back into a well-formed INI string, including section headers.

## Properties
- **config**: Holds the parsed configuration array from the last `parse_ini_string` call.
