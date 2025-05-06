# Class: ISPConfigRemotingHandlerBase

Base class for remoting (remote API) handlers in ISPConfig. Loads and manages remoting classes and their methods.

## Methods

- **__construct()**
  - Loads main remoting file and all remoting classes, registering their methods.
- **load_remoting_classes($glob_pattern)**
  - Loads remoting classes from given file pattern and registers their methods.
