
---
# Introduction to Rust

[Back to index](../README.md)

---
## Compiler
A rust file (`.rs`) can be compiled with the command `rustc my_program.rs` 
Then a binarie `my_program.exe`in windows or `my_program` in linux will be created.
It can be executed with `.\my_program.exe` in windows or `./my_program` in linux.

## Cargo
Cargo is Rust’s build system and package manager.
- The version installed can be checked: `cargo --version`
- To create a new project: `cargo new my_project`
- To compile the project: `cargo build`
- To run the project (will also buid if needed): `cargo run`
- To check if the program compiles without actually doing it: `cargo check`

## Some details
- Project names must be in lowercase separed by underscores ( `_` ).
- Each cargo project must have a ``src`` folder.
- There must be a ``main.rs`` file with a ``main()`` function inside ``src``.
- When the project is compiled a ``target`` folder is made.

## Format
Rust can also auto-format the code to follow the convention with `rustfmt my_program.rs`.