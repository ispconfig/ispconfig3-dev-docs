# Class: system

Provides system-level utilities and checks for ISPConfig, such as verifying available services for users and managing server configuration state.

**Source File:** interface/lib/classes/system.inc.php

## Properties
- **client_service**: Cached client service information retrieved per user.
- **_last_exec_out**: Array of output lines from the last executed safe command.
- **_last_exec_retcode**: Return code from the last executed safe command.
- **server_count**: Cached counts of enabled server types (mail, web, dns, etc.).

## Methods
- **has_service($userid, $service)**
  - Determines if the specified user has access to the given service, based on enabled servers and client settings.
- **is_blacklisted_web_path($path)**
  - Checks if a web path's first segment is in a reserved blacklist (e.g., `cgi-bin`, `etc`, `usr`).
- **rmdir($path, $recursive = false)**
  - Safely removes a directory; optional recursive deletion; prevents root directory removal.
- **last_exec_out()**
  - Returns the array of output lines captured from the last `exec_safe` call.
- **last_exec_retcode()**
  - Returns the return code from the last `exec_safe` call.
- **exec_safe($cmd, ...$args)**
  - Executes a shell command with placeholders safely, escaping arguments and storing output/return code.
- **system_safe($cmd, ...$args)**
  - Executes a shell command safely via `exec_safe` and returns combined output as a string.
- **is_installed($appname)**
  - Checks if the specified application is installed by running `which` and evaluating the return code.

## Usage
Used internally by ISPConfig to perform system-level checks, safely execute commands, and verify service access for users.
