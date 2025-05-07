# ISPConfig Database Schema and SQL Files

ISPConfig uses a MySQL/MariaDB database to store configuration and runtime data for all managed services.

## Main SQL File: `install/sql/ispconfig3.sql`
- This file contains the **complete database schema and initial data** for a fresh ISPConfig installation.
- When you install ISPConfig, this SQL file is imported to create all required tables, fields, indexes, and default values.
- If you add or modify a database field or table in ISPConfig, you must update this file to reflect your changes.

## How to Make Database Changes (for Developers)

1. **Edit `ispconfig3.sql`**
   - Add new tables or fields directly to this file. It should always represent the latest full schema for new installations.

2. **Edit `incremental/upd_dev_collection.sql`**
   - Add the corresponding `ALTER TABLE`, `CREATE TABLE`, or `UPDATE` statements (in MySQL syntax) to this file.
   - This file contains all schema modifications made since the last ISPConfig release.
   - Append your changes at the end—do not remove or rewrite previous statements.

3. **Release Process**
   - On a new ISPConfig release, the contents of `upd_dev_collection.sql` are moved to a numbered patch file (e.g., `upd_0001.sql`, `upd_0002.sql`).
   - Each patch file is executed once per installation. Never modify existing (already-released) patch files, as they will not be re-applied.
   - After a patch runs, the `dbversion` field in the `server` table is updated to match the latest patch version.

4. **Testing Patch Files**
   - For development/testing, you can re-run a patch by lowering the `dbversion` in the `server` table to a value below your patch number.

## Incremental Patch Support
- Incremental patches are supported for ISPConfig versions **3.0.3 and later**.
- For versions prior to 3.0.3, only the full update method is available (the entire schema is reapplied).

## Location
- The SQL schema and patch files are located in: `install/sql/`
    - `ispconfig3.sql` — full schema
    - `incremental/` — incremental update scripts (patches)

## Database Schema Documentation
- Comprehensive documentation for all tables in the ISPConfig database is available in the [database_schema](database_schema/index.md) directory.
- Each table has its own documentation file with details about:
  - Table purpose and description
  - Complete schema with column details
  - Relationships to other tables
  - Additional notes about usage and functionality

## Best Practices
- Always keep `ispconfig3.sql` up to date with the latest schema.
- Never modify already-released patch files.
- Add new changes to the end of `upd_dev_collection.sql` during development.
- Document your changes and test updates on a development system before release.
- Refer to the [Database Schema Documentation](database_schema/index.md) for detailed information about all tables in the ISPConfig database.

---

For more details, see `install/sql/README.txt` in the ISPConfig source tree.
