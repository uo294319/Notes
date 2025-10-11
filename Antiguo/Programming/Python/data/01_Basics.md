
---
# 01 Basics

[Back to index](../README.md)

---

## Datatypes

- `int`          whole number
- `float`       number with decimals
- `str`           string value
- `bool`        boolean:   False/True

```python
str(myValue)      #Convert to string
int(myValue)      #Convert to integer
float(myValue)    #Convert to float
```

Find out the datatype with:    `type(myValue)`

## Operators

### Logical, relational and boolean
| Operator | Description           |
| -------- | --------------------- |
| `>`      | Greater than          |
| `<`      | Lower than            |
| `<>`     | Greater or lower than |
| `==`     | Equal to              |
| `!=`     | Not Equal to          |
| `and`    | Logic “AND”           |
| `or`     | Logic “OR”            |
| `not`    | Logic “NOT”           |
    

## Aritmetical

| Operator | Description               |
| -------- | ------------------------- |
| `+`      | Addition                  |
| `-`      | Substraction              |
| `*`      | Multiplication            |
| `/`      | Float division            |
| `//`     | Int division              |
| `%`      | Remainder of int division |
| `**`     | Power                     |
    
## Increment y decrement

| Operator | Equivalent   |
| -------- | ------------ |
| `x += n` | `x = x + n`  |
| `x -= n` | `x = x - n`  |
| `x *= n` | `x = x * n`  |
| `x /= n` | `x = x / n`  |
    

## Variables

```python
myVariable = 1        #Int
myVariable = 1.0      #Float
myVariable = "1"      #String
```

## Constantes

```python
# There is no integrated constants in python.
# Uppercase used in its name to diferenciate them.
CONSTANT = 3
```

## Usefull functions

```python
chr(65)          -->  'A'        # ASCII to char
ord('A')         -->   65        # char to ASCII

hex(256)         -->  '0x100'    # int to hex
int('1B', 16)    -->   27        # hex to int

bin(4)           -->  '0b100'    # int to bin
int('0b100', 2)  -->   4        # bin to int
```

```python
max(a, b, c)     # return max value
min(a, b, c)     # return min value

round(num, n)    # rounds num to n decimal parts
```