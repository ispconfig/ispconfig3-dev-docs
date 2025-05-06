# Class: remoting_server

Handles server-related remote API functions in ISPConfig. Extends the base remoting class.

## Methods

- **server_get_serverid_by_ip($session_id, $ipaddress)**
  - Returns the server ID for a given IP address.
- **server_get_all($session_id)**
  - Returns a list of all servers.
- **server_update($session_id, $server_id, $params)**
  - Updates the configuration for a server.
