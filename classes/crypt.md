# Class: crypt

Provides cryptographic utilities for ISPConfig, including password encoding for PostgreSQL.

## Methods
- **postgres_scram_sha_256($password)**
  - Encodes a password using the SCRAM-SHA-256 algorithm for PostgreSQL. Generates a salt and returns the encoded string in the required format.
