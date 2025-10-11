
---
# 03 Formatting

[Back to Java index](../README.md)

---

## **Format**

```java
String myString = String.format("...", myVariable)

System.out.printf("...", myVariable)

    `%d`       integer
    `%s`       string
    `%f`       float
    `%x`       hexadecimal
    `%c`       char
    `%o`       octal
```

## **Special characters**

    `\’`     Single quotation mark
    `\”`     Double quotation mark
    `\\`     Backslash
    `\t`     Tab
    `\b`     Backspace
    `\r`     Carriage return (vuelta al comienzo)
    `\f`     Formfeed
    `\n`     Newline

## **String ↔ numbers**

```java
// String to numbers
int    myInt    = Integer.parseInt(myString)
float  myFloat  = Float.parseFloat(myString)
double myDouble = Double.parseDouble(myString)

// anything to String
type myVar = value;
String myStr = myVar.toString();
```