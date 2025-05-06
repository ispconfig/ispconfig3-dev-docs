# Class: ISPConfigRESTHandler

Extends `ISPConfigRemotingHandlerBase` to implement REST API endpoints for ISPConfig. Handles API versioning, error and JSON responses, and dispatches remote methods.

## Properties
- **api_version**: The version of the REST API.

## Methods
- **_return_error($code, $codename, $message)**: Sends an HTTP error response with a message.
- **_return_json($code, $data = '')**: Sends an HTTP JSON or plain text response.

## Usage
This class is used to provide RESTful API access to ISPConfig's remote functions for integrations and automation.
