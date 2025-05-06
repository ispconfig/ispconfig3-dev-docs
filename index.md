# ISPConfig 3 Developer Documentation Index

ISPConfig is a powerful, open-source hosting control panel for Linux servers, allowing administrators and resellers to manage web, mail, DNS, database, and other services through a web-based interface.

## ISPConfig manages these services

- Web
- Mail
- DNS
- Database

## ISPConfig is built on these technologies

- PHP (PHP-CLI and PHP-FPM)
- Bash
- MariaDB or MySQL
- PostgreSQL (optional, for website databases only)
- Apache or Nginx
- Bind or PowerDNS
- Postfix
- Dovecot
- Pure-FTPd
- ClamAV
- Fail2Ban
- Mailman (deprecated)
- Roundcube

This documentation set provides detailed developer guides for the ISPConfig codebase and framework, covering:

- **Server Backend**: Guide to the server-side components of ISPConfig.
- **Web Interface**: Guide to the client-side components of ISPConfig.
- **Folder Structure**: Guide to the directory structure of ISPConfig. (See [Folder Structure](folder-structure.md))
- **Class Reference**: Complete API documentation for core classes (`interface/lib/classes`), explaining methods, properties, and usage examples. (See [Classes Reference](classes/index.md))
- **tform System**: Guide to the dynamic form framework, including field types, filters, validators, datasources, and template logic. (See [tform System](tform/index.md))
- **Template Engine**: Reference for the vlibTemplate system used by ISPConfig to render HTML templates with loops, conditionals, and includes. (See [Template Engine](tform/template-logic.md))

## Sub-Indicies
- [Classes Reference](classes/index.md)
- [Form (tform) Documentation](tform/index.md)
- [Folder Structure](folder-structure.md)
- [Template Engine](tform/template-logic.md)

Use these links to navigate to the specific areas of the codebase you need to understand or extend. For contributions, see the README and CONTRIBUTING files in the project root.
