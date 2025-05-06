# Class: auth

Handles authentication, authorization, and user/group management in ISPConfig.

**Source File:** interface/lib/classes/auth.inc.php

## Methods
- **get_user_id()**
  - Returns the current user's ID.
- **is_admin()**
  - Returns true if the current user has admin privileges.
- **is_superadmin()**
  - Returns true if the current user is the superadmin (user ID 1).
- **is_reseller()**
  - Returns true if the current user is a reseller.
- **has_clients($userid)**
  - Checks if the specified user has any client accounts.
- **is_client_of_reseller($userid = 0)**
  - Determines if a user belongs to a reseller.
- **add_group_to_user($userid, $groupid)**
  - Adds the specified group to the user's group list.
- **remove_group_from_user($userid, $groupid)**
  - Removes the specified group from the user's group list.
- **get_client_limit($userid, $limitname)**
  - Retrieves the specified client limit for a user; returns -1 for no limit.
- **verify_module_permissions($module)**
  - Checks if the user has read access to the given module.
- **check_module_permissions($module)**
  - Redirects or errors if the user lacks access to the given module.
- **check_security_permissions($permission)**
  - Checks and enforces specific security permissions.
- **get_min_password_length()**
  - Retrieves the minimum password length from configuration.
- **get_min_password_strength()**
  - Retrieves the minimum password strength requirement.
- **get_random_password($minLength = 8, $special = false)**
  - Generates a random password; includes special characters if true.
- **crypt_password($cleartext_password, $charset = 'UTF-8')**
  - Hashes a password using the specified charset and salt algorithm.
- **csrf_token_get($form_name)**
  - Generates and returns a CSRF token for the given form.
- **csrf_token_check($method = 'POST')**
  - Validates the CSRF token from the specified request method.

## Properties
- **client_limits**: Cached client limits for the current session.
