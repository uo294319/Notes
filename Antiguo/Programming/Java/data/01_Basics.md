
---
# 01 Basics

[Back to Java index](../README.md)

---

## **Datatypes**

- **Integers:**
    - `Byte`: 1 byte (-128 to 127)
    - `Short`: 2 byte (-32,768 to 32,767)
    - `Int`: 4 byte (order of 2,000M)
    - `Long`: 8 byte (suffixe L)
- **Floating point:**
    - `Float`: 4 byte (6-7 decimals) (suffixe F)
    - `Double`: 8 byte (15 decimals)
- Other:
    - `Char`: caracteres (simple quotes)
        - `String`: sequence of chars (double quotes)
    - `Boolean`: true/false

## **Variables y constantes**

```java
int variable;    //declaration
// variable is undefined
myInt = 1; // Initialize

final int CONSTANTE;
COSTANTE = 1;
```

## **Operadores**

- **Arithmetical:**
    
    `+`	Addition (concatenation)
    
    `-`    Substraction
    
    `*`    Multiplication
    
    `/`	division (type heritage)
    
    `%`	Rest
    
- **Logical:**
    
    `>` 	Greater than
    
    `<`	Lower than
    
    `<>`	Greater or lower than
    
    `!=`	Not equal to
    
    `==`	Equal to
    
    `&&`	Logical AND
    
    `||`	Logical OR
    
    `!(…)`   Logical NOT 
    
- **Increment & decrement:**
    
    `++`	Increment in 1
    
    `--`	Decrement in 1
    
    `+=n` Incremento in n
    
    `=n`	Decrement in n
    

## Especial Operator ( ? :)

```java
int a = (condition) ? 10:20;

//condition = true;  a = 10
//condition = false; a = 20
```