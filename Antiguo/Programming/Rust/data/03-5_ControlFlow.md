
---
# Control Flow

[Back to index](../README.md)

---
## Conditional structures

### `if` expressions
- Allows you to branch your code depending on conditions.
- We use the `if` keyword followed by the condition and the code between brackets.
- Optionally, you can specify what to do if the condition is not met with `else`.

```Rust
fn main() {
    if condition {
        println!("condition was true");
    } else {
        println!("condition was false");
    }
}
```

### `if` in a let statement
- The `if` can also be used after an variable declaration.
- Both returns must be of the same type.

```Rust
fn main() {
    let condition = true;

    let variable = if condition { 5 } else { "five" };
    let variable = if condition { 5 } else { 6 }; // Error

    println!("The value of number is: {number}");
}
```

## Repetitive structures

### Loops
- They are defined with the `loop` keyword.
- We can use the `break` keyword to end a loop.
- We can use the `continue` keyword to jump to the start of the loop.

```Rust
fn main() {
    loop { // Infinite loop
        println!("again!");
    }
}
```

#### Example of a loop returning a value
```Rust
fn main() {
    let mut counter = 0;

    let result = loop {
        counter += 1;

        if counter == 10 {
            break counter * 2;
        }
    };

    println!("The result is {result}");
}
```

#### Loop labels
- In order to differenciate a loop inside another we can provide a label.
- This is done by typing `'label: loop`.
- Note that the label starts by a single quote `'`.

```Rust
fn main() { // Here's an example
    let mut count = 0;
    'counting_up: loop {
        let mut remaining = 10;
        loop {
            if remaining == 9 {
                break;
            }
            if count == 2 {
                break 'counting_up;
            }
            remaining -= 1;
        }

        count += 1;
    }
    println!("End count = {count}");
}
```

### While loops
- This works similar to the `loop` keyword.
- The code will be repeated while a condition is met.

```Rust
fn main() {
    let mut number = 3;

    while number != 0 {
        println!("{number}!");
        number -= 1;
    }
}
```

### For loops
- It is possible to loop over a collection with a while.
    ```Rust
    fn main() {
        let a = [10, 20, 30, 40, 50];
        let mut index = 0;

        while index < 5 {
            println!(a[index]);
            index += 1;
        }
    }
    ```
- But it is easier to loop with the `for` keyword.

    ```Rust
    fn main() {
        let a = [10, 20, 30, 40, 50];

        for element in a {
            println!("the value is: {element}");
        }
    }
    ```
