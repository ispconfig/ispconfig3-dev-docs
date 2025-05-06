# Class: getconf

Provides methods to retrieve server, global, and security configuration settings from the ISPConfig database. Used throughout ISPConfig to access configuration data for different modules and servers.

**Source File:** interface/lib/classes/getconf.inc.php

## Methods
- **get_server_config($server_id, $section = '')**
  - Loads and caches a server's configuration from the `server` table and returns the full array or the specified section.
- **get_global_config($section = '')**
  - Loads and caches global configuration from the `sys_ini` table and returns the full array or the specified section.
- **get_security_config($section = '')**
  - Loads and caches security settings from `security_settings.ini` and returns the full array or the specified section. (Moved to `$app->get_security_config`.)

## Properties
- **config**: Cache storage for server and global configuration arrays.
- **security_config**: Cache storage for security configuration settings array.
