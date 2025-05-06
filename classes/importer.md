# Class: importer

Handles the import of data into ISPConfig, extending the remoting interface for bulk or scripted operations. Uses a `fakeserver` instance to simulate server-side operations and prevent remote login.

## Methods
- **__construct()**
  - Initializes the importer with a fake server instance.
- **login($username, $password)**
  - Overridden to disable remote login for importer scripts.

## Usage
Use this class for importing data into ISPConfig programmatically, ensuring that remote login is not possible during import operations.

## Related Classes
- **fakeserver**: Used internally to simulate server operations and handle fault messages.
