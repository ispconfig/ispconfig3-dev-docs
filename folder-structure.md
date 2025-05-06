# ISPConfig Directory Structure

ISPConfig has two main components:

1. **Server Backend** (services, daemons, CLI tools)
2. **Web Interface** (PHP-based admin interface)

---

## 1. Server Backend

The server backend can be found in the `/usr/local/ispconfig/server/` directory. It contains scripts, background services, and API endpoints that power ISPConfig's core functionality.

```bash
server/
├── aps_packages/        # APS packaging resources and definitions (deprecated)
├── cli/                 # Command-line interface tools
│   ├── ispc             # CLI shell script wrapper
│   ├── ispc.php         # Main PHP CLI entry point
│   └── modules/         # CLI modules
│       ├── extension.inc.php   # ISPConfig extension management
│       ├── help.inc.php        # CLI help generator
│       ├── letsencrypt.inc.php # Let's Encrypt integration
│       ├── php.inc.php         # PHP module helper
│       ├── update.inc.php      # Update management
│       ├── user.inc.php        # User management
│       └── version.inc.php     # Version info
├── conf/                # Default configuration templates
├── conf-custom/         # Custom configuration overrides
├── lib/                 # Server-side libraries and classes
│   ├── app.inc.php      # Application bootstrap and global helpers
│   ├── compatibility.inc.php # Backwards compatibility utilities
│   └── classes/         # Core server classes and libraries
│       ├── aps_base.inc.php      # APS service base class (deprecated)
│       ├── backup.inc.php        # Backup management
│       ├── cli.inc.php           # CLI dispatch logic
│       ├── cron.d/               # Cron job definitions
│       ├── tpl.inc.php           # Template engine core
│       └── ...                   # Other class files
├── mods-available/      # Available server modules
├── mods-core/           # Core server modules
├── mods-enabled/        # Enabled server modules (symlinks)
├── plugins-available/   # Available plugins
├── plugins-enabled/     # Enabled plugins (symlinks)
├── scripts/             # Daemon and script utilities
└── temp/                # Temporary files and caches
```

## 2. Web Interface

All PHP and web assets live under the `/usr/local/ispconfig/interface/` folder:

```bash
interface/
├── acme/                  # ACME (Let's Encrypt) challenge response scripts
├── cache/                 # Compiled template and data cache
├── lib/
│   ├── app.inc.php              # Application bootstrap and global helpers
│   ├── classes/                 # Core PHP classes and libraries
│   ├── compatibility.inc.php    # Backwards compatibility utilities
│   ├── config.inc.php           # Main configuration file (DB credentials, paths) for the UI
│   ├── lang/                    # Global language files (en.lang, de.lang, ...)
│   ├── plugins/                 # Interface plugins
│   ├── server_conf.master       # Template for server-specific configuration
│   └── shelluser_blacklist      # Blacklist for shell user creation
├── ssl/                  # SSL Certificates for the UI and apps vhost
├── temp/                  # Temporary files and uploads
├── tools/                 # CLI and maintenance scripts
└── web/
    ├── js/                # JavaScript assets
    ├── themes/            # CSS, images, layout templates
    ├── admin/             # Admin interface module
    ├── client/            # Client interface module
    ├── dashboard/         # Summary dashboard module
    ├── dns/               # DNS management module
    ├── help/              # Help and documentation module
    ├── login/             # Login module
    ├── mail/              # Mail server module
    ├── mailuser/          # Mailuser login module
    ├── monitor/           # Monitoring and status module
    ├── remote/            # Remote API endpoint
    ├── sites/             # Website management module
    ├── strengthmeter/     # Password strength meter code
    ├── temp/              # Temporary web scripts
    ├── tools/             # Web-based tools and utilities
    ├── vm/                # OpenVZ Virtual machine management module (deprecated)
    └── <other>/...        # Other modules
```

### Notes on Module Structure
- **Modules**: Each folder under `web/` (e.g. `mail`, `sites`) implements a distinct ISPConfig feature.
- **Forms**: Definitions in `form/` use the tform system (`*.tform.php`).
- **Templates**: HTML templates of forms and lists live in `templates/`.
- **Language**: Core translations live in `interface/lib/lang/`; modules can override or extend in `web/<module>/lib/lang/`.
- **List**: List scripts live in `list/`.

Use this map to locate configuration files, class definitions, and module resources when developing or extending ISPConfig.
