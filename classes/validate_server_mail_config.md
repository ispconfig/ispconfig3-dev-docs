# Class: validate_server_mail_config

Validator for server mail configuration fields in ISPConfig.

## Methods

- **get_error($errmsg)**
  - Returns a localized error message for mail config validation.
- **mailbox_virtual_uidgid_maps($field_name, $field_value, $validator)**
  - Validates changes to the `virtual_uidgid_maps` setting, ensuring consistency and correct server/user state.
