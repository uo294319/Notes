
---
# 03 Tuples Management

[Back to index](../../README.md)

---
## Inserting tuples

- Syntax: `INSERT INTO [table] VALUES( [values ...] )`
```postgresql
-- table1 is a table with 3 properties.
-- value1, value2 and value3 must have the proper datatypes.
INSERT INTO table1 VALUES(value1, value2, value3);
```

## Delete tuples
- Syntax: `DELETE FROM [table] WHERE [condition]`
```postgresql
-- Delete from table1 the second tuple
DELETE FROM table1 WHERE table1_id = 2;

-- Delete all tuples of table1 
DELETE FROM table1;
```

## Update tuples

- Syntax: `UPDATE [table] SET [propertie = new value] WHERE [condition]`
```postgresql
-- Set property name of all tuples of table1 to "A"
UPDATE table1 SET table1_name = "A";

-- Set property name of second tuple of table1 to "B"
UPDATE table1 SET table1_name = "B" WHERE table1_name = 2;
```
