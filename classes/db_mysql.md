# Class: db

Provides the MySQL database interface for ISPConfig, handling connections, queries, escaping, and error management. Used throughout ISPConfig for database operations.

**Source File:** interface/lib/classes/db_mysql.inc.php

## Methods
- **__construct($host = NULL, $user = NULL, $pass = NULL, $database = NULL, $port = NULL, $flags = NULL)**
  - Initializes a database connection using provided or default parameters.
- **__destruct()**
  - Closes the database connection on object destruction.
- **close()**
  - Explicitly closes the current database connection.
- **testConnection()**
  - Tests if the current database connection is valid.
- **__get($var)**
  - Allows private variables to be accessed outside the class.
- **_build_query_string($sQuery = '')**
  - Builds a query string with proper escaping and formatting for arguments.
- **_setCharset()**
  - Sets the MySQL client connection charset based on the configured dbCharset.
- **securityScan($string)**
  - Scans and sanitizes input strings to prevent SQL injection.
- **_query($sQuery = '')**
  - Executes raw SQL queries and returns a `db_result` object for result handling.
- **query($sQuery = '')**
  - Builds and executes a SQL query with argument substitution.
- **queryOneRecord($sQuery = '', ...$params)**
  - Executes a query and returns the first row as an associative array.
- **queryOne($sQuery = '', ...$params)**
  - Alias for `queryOneRecord()`.
- **query_one($sQuery = '', ...$params)**
  - Legacy alias for `queryOneRecord()`.
- **queryAllRecords($sQuery = '', ...$params)**
  - Executes a query and returns all result rows as an array of associative arrays.
- **queryAll($sQuery = '', ...$params)**
  - Alias for `queryAllRecords()`.
- **query_all($sQuery = '', ...$params)**
  - Legacy alias for `queryAllRecords()`.
- **queryAllArray($sQuery = '', ...$params)**
  - Executes a query and returns the first column of all result rows as a simple array.
- **query_all_array($sQuery = '', ...$params)**
  - Legacy alias for `queryAllArray()`.
- **insert_id()**
  - Returns the ID of the last inserted row (auto-increment).
- **affected()**
  - Returns the number of rows affected by the last query.
- **check_utf8($string)**
  - Validates if a string is valid UTF-8.
- **escape($sString)**
  - Escapes special characters in a string for use in SQL queries.
- **_sqlerror($sErrormsg = 'Unbekannter Fehler', $sAddMsg = '', $bNoLog = false)**
  - Internal handler for SQL errors, optionally logs or suppresses messages.
- **affectedRows()**
  - Alias for `affected()`.
- **insertID()**
  - Alias for `insert_id()`.
- **quote($formfield)**
  - Wraps and escapes a string for safe SQL insertion (quotes the value).
- **unquote($formfield)**
  - Removes surrounding quotes from a string.
- **getDatabaseVersion($major_version_only = false)**
  - Retrieves the MySQL server version; optionally returns only the major version.
- **getPasswordHash($password, $hash_type = 'mysql_native_password')**
  - Generates a password hash for the given password using the specified hashing algorithm.
- **genSalt($size)**
  - Generates a random salt of the given byte length for password hashing.

## Properties
- **dbHost, dbPort, dbName, dbUser, dbPass, dbCharset, dbClientFlags**: Connection parameters.
- **show_error_messages**: Controls error message display.
- **errorNumber, errorMessage**: Last error state.

## Related Classes
- **db_result** (from `db_mysql.inc.php`):
  - **rows()**: Returns the number of rows in the result set.
  - **affected()**: Returns the number of rows affected by the last query.
  - **free()**: Frees the result set resources.
  - **get()**: Fetches the next row as an associative array.
  - **getAsRow()**: Fetches the next row as a numeric array.
- **fakedb_result** (from `db_mysql.inc.php`):
  - **rows()**: Returns the number of rows in the fake result set.
  - **free()**: Clears the internal data arrays.
  - **get()**: Fetches the next fake row as an associative array.
  - **getAsRow()**: Alias for `get()`.
  - **limit_result($iStart, $iLength)**: Limits the result set by offset and length.
