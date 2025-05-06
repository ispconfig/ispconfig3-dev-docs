# Class: ISPConfigRESTHandler

Handles REST API requests in ISPConfig. Extends `ISPConfigRemotingHandlerBase`.

## Methods

- **run()**
  - Handles incoming HTTP requests, determines the method (GET, POST, etc.), and dispatches to the appropriate handler.
- **_return_error($code, $codename, $message)**
  - Sends an HTTP error response with the given code and message.
- **_return_json($code, $data = '')**
  - Sends a JSON response with the given code and data.
