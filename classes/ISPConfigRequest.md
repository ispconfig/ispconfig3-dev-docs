# Class: ISPConfigRequest

Abstract base class for HTTP requests and response handling in ISPConfig.

## Methods

- **get_with_headers($url, $store_in = null, $follow_redirects = false, $user_agent = false)**
  - Fetches headers and content from a URL, optionally storing the response in a file. Handles redirects and user agent customization.
