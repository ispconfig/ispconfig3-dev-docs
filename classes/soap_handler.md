# Class: ISPConfigSoapHandler

Extends `ISPConfigRemotingHandlerBase` to implement SOAP API endpoints for ISPConfig. Handles dynamic method dispatching to registered remoting classes and methods, and manages SOAP faults.

## Methods
- **__call($method, $params)**: Dynamically calls the appropriate method on the remoting class, handling errors and SOAP faults as needed.

## Usage
This class is used to provide SOAP-based remote access to ISPConfig functions for integrations and automation.
