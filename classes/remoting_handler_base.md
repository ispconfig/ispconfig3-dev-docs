# Class: ISPConfigRemotingHandlerBase

Base class for ISPConfig remoting handlers. Loads and registers remoting classes and methods, including those from modules. Creates main remoting class and manages method dispatching.

## Properties
- **methods**: List of available remote methods.
- **classes**: Instantiated remoting classes.

## Methods
- **__construct()**: Loads main remoting file and all remoting classes, registers methods.
- **load_remoting_classes($glob_pattern)**: Loads remoting classes from specified paths.

## Usage
This class is extended by specific handlers (e.g., SOAP, REST) to provide API endpoints for ISPConfig remote access.
