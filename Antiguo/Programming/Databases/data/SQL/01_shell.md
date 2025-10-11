
---
# 01 PSQL shell commands

[Back to index](../../README.md)

---
## Basic

- Get help: `\?`
- Salir del intérprete: `\q`
- Connect to a database: `\c dbname username`
- Command history: `\s`
## Databases
- List all databases: `\l`
- List available functions in the current database: `\df`
- Execute PSQL commands from a file: `\i filename`
- Remove a database: `drop database database_name`

> [!WARNING]
> Is not possible to delete the currently active database.
## Tables
- List all tables: `\dt`
- Describe a table: `\d table_name`
- List available views: `\dv`