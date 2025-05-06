# Class: validate_dns

Validator for DNS-related fields in ISPConfig.

## Methods

- **validate_field($field, $area, $zoneid, $wildcard_allowed = 1)**
  - Validates a DNS field (name, data, etc.) for correctness.
- **validate_rr(&$rr)**
  - Validates a DNS resource record array for correctness and completeness.
