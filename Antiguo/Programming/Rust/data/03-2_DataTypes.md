
---
# Data types

[Back to index](../README.md)

---

## Introduction

- Rust must know the types of all variables at compile time.
- The compiler can usually infer the type.
- In cases when many types are possible, it must be specified.
    ```Rust
    let var: datatype;
    ```
- There are two main types: scalar and compound.

## Scalar
Are tupes that represent a single value

### Integer
|Length   | Signed | Unsigned |
|---------|--------|----------|
| 8-bit   | i8     | u8       |
| 16-bit  | i16    | u16      |
| 32-bit  | i32    | u32      |
| 64-bit  | i64    | u64      |
| 128-bit | i128   | u128     |
| arch    | isize  | usize    |

- `arch` depends on the architecture (64-bit or 32-bit)
- Signed integers are stored using two's complement.
- By default: `i32`.
- Can be specified in Dec (`14`), Hex (`0x e`), Octal (`0o 16`) or Bin (`0b 1110`).
- If `u8`, also expressed as Byte (`b'E'`)

### Floating point
- As the integers there exist from `f8` to `f128` (varying the size).
- All floating point values are signed.
- By default: `f64`

### Boolean
- Can be `true` or `false`.
- Explicitely defined with `bool`.

### Character
- Explicitely defined with `char`.
- Characters use simple quotes (`'A'`).
- It is 4-byte wide represented in Unicode Scalar Value

## Compound
Are a way of grouping multiple values into one type

### Tuple
- Can contain together a number of values with a variety of types.
- We create a tuple by writing a comma-separated list of values inside parentheses.

```Rust
let tup = (500, 6.4, 1);  // Explicitely defined type ->  tup: (i32, f64, u8)
let (x, y, z) = tup;      // x = 500 , y = 6.4 , z = 1
let value = tup.1         // Access the index 1 -> value = 6.4
```

### Array
- Allows to collect a number of values of the same type.
- It has a fixed size
- We write the values in an array as a comma-separated list inside square brackets.

```Rust
let a = [1, 2, 3, 4, 5];  // Explicitely defined type-> a: [i32; 5]
let value = a[1];         // Access index 1 -> value = 2
```
