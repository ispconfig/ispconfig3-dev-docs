# Class: remoting

Handles remote procedure calls (RPC) for ISPConfig, supporting SOAP and remote API access. Manages session timeouts, method registration, and user data context for remote operations.

## Properties
- **session_timeout**: Remote session timeout in seconds.
- **oldDataRecord, dataRecord, id**: Used for storing and managing record data in RPC context.
- **_methods**: Registered remote methods.

## Methods
- **__construct($methods = array())**: Initializes remoting with a list of available methods.

## Usage
This class is used to provide remote access to ISPConfig functions for integrations and automation via SOAP or other remote APIs.
