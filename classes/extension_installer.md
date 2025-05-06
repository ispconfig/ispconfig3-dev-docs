# Class: extension_installer

Handles the installation, update, removal, and management of ISPConfig extensions from the official repository.

## Methods
- **getRepoListUrl()**
  - Returns the repository list URL, optionally with a dev key if present.
- **addError($error)**
  - Adds an error message to the internal error list.
- **getErrors()**
  - Returns the list of error messages.
- **hasErrors()**
  - Returns true if there are errors.
- **getRepoExtensions()**
  - Fetches the list of available extensions from the repository (with caching).
- **getRepoExtension($name)**
  - Returns details for a single extension from the repository by name.
- **getInstalledExtensions($server_id = null)**
  - Gets a list of installed extensions on a server (or all servers).
- **getInstalledExtension($name, $server_id)**
  - Gets details for a specific installed extension.
- **installExtension($name, $server_id)**
  - Initiates the installation of an extension on a server.
- **updateExtension($name, $server_id)**
  - Initiates the update of an installed extension.
- **deleteExtension($name, $server_id)**
  - Initiates the removal of an installed extension.
- **enableExtension($name, $server_id)**
  - Enables an installed extension on a server.
- **disableExtension($name, $server_id)**
  - Disables an installed extension on a server.

## Properties
- **repo_list_url**: URL for the extension repository API.
- **extension_basedir**: Local base directory for extensions.
- **error**: Array of error messages.
- **repo_cache**: Cached repository extension list.
