# Class: session

Manages user sessions in ISPConfig, including session data storage, timeout, and permanence. Implements PHP session handler methods for opening, closing, reading, and writing sessions.

## Properties
- **session_array**: Stores session data.
- **db**: Database connection for session storage.
- **timeout**: Session timeout duration.
- **permanent**: Whether the session is permanent.

## Methods
- **__construct($session_timeout = 0)**: Initializes the session handler.
- **set_timeout($session_timeout = 0)**: Sets the session timeout.
- **set_permanent($value = false)**: Sets session permanence.
- **open($save_path, $session_name)**: Opens a session.
- **close()**: Closes a session.

## Usage
Used internally by ISPConfig to manage PHP sessions, supporting custom session handling and timeouts.
