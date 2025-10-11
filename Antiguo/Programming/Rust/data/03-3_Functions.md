
---
# Functions

[Back to index](../README.md)

---

## Introduction
- Functions are declared with the `fn` keyword followed by the function name.
- By convention they are written in lowercase with words separed by underscores.
- Most important function is `main` which is the entry point for the program.

```Rust
fn main() {
    println!("Hello, world!");
    another_function();
}

fn another_function() {
    println!("Another function.");
}
```

## Parameters
- Parameters (or arguments) are values passed to the function.
- The type of the parameters must be specified.
- If there are several parameters they are separed by commas.
```Rust
fn main() {
    function1(5);
    function1(5, 7);
}

fn function1(x: i32) {
    println!("The value of x is: {x}");
}

fn function2(x: i32, y: i32) {
    println!("x == {x} and y == {y}");
}
```

## Statements and Expressions
- Statements are instructions that perform some action and do not return a value.
- Expressions evaluate to a resultant value. They do not end in `;`.

```Rust
fn main() {
    let y = {         // Inner scope
        let x = 3;    // Define a variable x
        x + 1         // Expression. Return x + 1.
    };

    println!("The value of y is: {y}");    // y = 4
}
```

## Functions and return values
- Functions can return values to the other one that calls them.
- We do not name the return value.
- We must specify the return type with `->` followed by the type.
- W



```Rust
fn main() {
    let x = five(); // Now x = 5
    let y = plus_one(x); // Now y = x + 1 = 6
}

fn five() -> i32 {  // Specify the return value
    5 // This is an expression
}

fn plus_one(x: i32) -> i32 {
    x + 1 // This is an expression
}
```
