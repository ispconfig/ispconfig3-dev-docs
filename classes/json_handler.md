# Class: ISPConfigJSONHandler

Implements a JSON-based API handler for ISPConfig, extending the remoting handler base. Processes incoming JSON requests, maps them to available methods, and returns JSON-formatted responses.

## Methods
- **run()**
  - Main entry point for handling a JSON API request. Parses the method and parameters, validates input, and dispatches the call.
- **_return_json($code, $message, $data = false)**
  - Sends a JSON response with the specified status code, message, and optional data.

## Usage
This class is used to provide a JSON API endpoint for ISPConfig, allowing external clients to interact with ISPConfig using JSON requests and responses.
