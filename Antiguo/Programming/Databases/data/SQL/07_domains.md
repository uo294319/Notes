
---
# 07 Domains

[Back to index](../../README.md)

---
## Definition
- Is a data type with some optional restrictions.

```postgresql
CREATE DOMAIN domain_name AS data_type
[COLLATE collation] [DEFAULT expression] [constraint […]]
```

- The collation is a function that defines the comparation for ordering rows.
- The constraint can be:
	- `NULL`
	- `NOT NULL`
	- `CHECK(...)`

## Checking text patterns
```postgresql
CHECK( value ~ 'pattern')

-- Email example
CHECK( value ~ '^\w+@[a-zA-Z_]+?\.[a-zA-Z]{2,3}$');
```

- `^` is used to represent the start of the string.
- `$` is used to represent the end of the string.
- `+` is used to specify a sequence of 1 or more of the preceding character.

- `%` is used to represent any sequence of 0 or more characters.
- `_` is used to represent any character (only one).

- `\w` is used to represent any alphanumeric character or `_`.
- `a-z` are used to represent a character between `a` and `z`.
- `[ ... ]` is used to represent any of the characters inside (only one).
- `{ n }` is used to represent a sequence of `n` of the preceding character.