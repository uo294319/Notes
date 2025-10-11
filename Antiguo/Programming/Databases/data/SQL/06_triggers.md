
---
# 06 Triggers

[Back to index](../../README.md)

---
## Creation
```postgresql
CREATE TRIGGER trigger_name
{ BEFORE | AFTER } { operation }
ON table_name [ FOR EACH ROW | FOR EACH STATEMENT ] [ WHEN ( condition ) ]
EXECUTE PROCEDURE func_name (args)
```

- `operation` can be `INSERT`, `UPDATE` or `DELETE`. Several can be specified with `OR`.
---
## Variables
- `NEW` contains the new row (insert/update).
- `OLD` contains the old row (delete/update).
- `TG_WHEN` returns `BEFORE` or `AFTER`.
- `TG_LEVEL` returns `ROW` or `STATEMENT`.
- `TG_OP` returns `INSERT`, `UPDATE` OR `DELETE`.
- `TG_TABLE_NAME` returns the modified table.
---
## Levels
### STATEMENT-level
- Executed once per operation.
	- No matter the number of rows modified.
	- Always returns null.
```postgresql
CREATE OR REPLACE FUNCTION func_name() RETURNS trigger AS
$$
	BEGIN
		...
		RETURN NULL; -- Mandatory
	END;
$$ LANGUAGE 'plpgsql';

CREATE TRIGGER trigger_name
BEFORE {operation} ON table_name FOR EACH STATEMENT
EXECUTE PROCEDURE func_name();
```
### ROW-level + BEFORE
- Trigger is called for every row the operation modifies.
- Function is executed before the row modification.
	- The new value can be modified.
- Function must return the new row value.
	- Modified using variable `NEW`.
	- If `NULL` is returned, the row is not modified.
	
```postgresql
CREATE OR REPLACE FUNCTION func_name() RETURNS trigger AS
$$
	BEGIN 
		...
		RETURN NEW; -- New row values
	END;
$$ LANGUAGE 'plpgsql';

CREATE TRIGGER trigger_name
BEFORE {operation} ON table_name FOR EACH ROW
EXECUTE PROCEDURE func_name();
```

### ROW-level + AFTER
- Trigger is called for every row the operation modifies.
- Function is executed after the row modification.
	- The new value cannot be modified.
- The return value is not used.

```postgresql
CREATE OR REPLACE FUNCTION func_name() RETURNS trigger AS
$$
	BEGIN 
		...
		RETURN NULL; -- Does not matter
	END;
$$ LANGUAGE 'plpgsql';

CREATE TRIGGER trigger_name
AFTER {operation} ON table_name FOR EACH ROW
EXECUTE PROCEDURE func_name();
```
---