
---
# 06 Arrays

[Back to Java index](../README.md)

---

## Simple Array

```java
type[] myArray = new type[size]
// default values are 0 or null depending on the type

// Examples
char[] myArr = new char[3]
myArr[0] = 'a'
myArr[1] = 'b'
myArr[2] = 'c'

char[] myArr = { 'a' , 'b' , 'c' }

>>> { 'a' , 'b' , 'c' }
```

## Important

- If we use `=` between two arrays we will copy the **memory address**, NOT the **value**
    - To copy the value we must assign all elements one by one (usually with a for loop)
    - `clone()` method could also be used: `type[] newArr = oldArr.clone()`
- An array of arrays could be created:
    - **Matrix**:    `type[][]   = new type[size1][size2]`
    - **Tensor**:    `type[][][] = new type[size1][size2][size3]`

## Matrix Example

```java
int[][] myArr = { {1,2,3} , {4,5,6} , {7,8,9} }

/*
*   This matrix can be interpreted in two ways:
*   | 1 2 3 |        | 1 4 7 |
*   | 4 5 6 |   or   | 2 5 8 |
*   | 7 8 9 |        | 3 6 9 |
*/

// All these expressions are true
myArr[0] == {1,2,3}
myArr[0][0] == 1
myArr[2][1] == 8
```