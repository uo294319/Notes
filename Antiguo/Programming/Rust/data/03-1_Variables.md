
---
# Variables and Mutability

[Back to index](../README.md)

---

## Variables
- Variables are defined with the keyword `let`.
- By convention they are written in lower case but the first letter of each word (camelCase).
- By default they are inmmutable.
```Rust
let myVariable = 5;    // It should be let mut myVariable = 5
myVariable = 6;        // Error, immutable variable.
```
- They are made mutable with the keyword `mut`.
```Rust
let mut myVariable = 5;
myVariable = 6;    // now the value has changed
```

## Shadowing
- This allows to redefine a variable with the same name and a another value.
- This value will only be used in the scope it was redefined in.
  
```Rust
let x = 5;

    { // This is called a scope.
        let x = x * 2;
        // x inside this scope will be 10.
        // Note that before the assignment we can access the outside x.
    }
// Here x will be 5 again

// I can also redefine the variable in the same scope.
// The previous value of x is now forgotten.
let x = 7;
```

## Constants
- Constants are defined with the keyword `const`.
- By convention they are writen in capital letters separed by underscores.
- They cannot be modified nor redefined or shadowed.
```Rust
const MY_CONSTANT = 7;
const MY_CONSTANT = 3;  // Error.
```