
---
# 11 Exceptions

[Back to Java index](../README.md)

---
## Introduction
An Exception is a object of the type `Throwable`.
When one is thrown, the method that was currently executing is interrupted and the exception is passed to the previous function, which passes again the exception to the previous one and so on until a method with the correct treatment of exceptions is reached.

The exceptions have the following hierarchy of classes:
- `Throwable`
    - `Exception`
        - `IOException`
        - `RuntimeException`
            - `ClassCastException`
            - `IndexOutOfBoundsException` (`ArrayIndexOutOfBoundsException`)
            - `NullPointerException`
            - `NoSuchElementException` (`InputMismatchException`)
            - `ArithmeticException`
    - `Error`
        - `AWTError`
        - `ThreadDeath`
        - `VirtualMachineError`

Exceptions can be thrown automatically by the Java Virtual Machine (JVM) or manually by the developer using the sentence `throw` when we know a method can throw a Exception we should add after its declaration `throws Exception`.  

```java
public static int exampleMethod throws ArithmeticException (int num, int den) {
    // If b=0 the division can not be done -> exception
    return num/den;
}
```
## try-catch-finally

```java
try {
    // Here goes the code fragment that can provoke a Exception
} catch (Exception e) {
    // If a exception of the type indicated happens in try block
    // this fragment of code is executed
    // The variable e contains the exception thrown by try block
    // There can be multiple catch blocks with diferent exceptions.
} finally {
    // This code fragment is executed always.
}
```
## Class Exception

The class `Exception` has some methods:
- `Throwable getCause()`
    Returns the object Throwable that indicates the cause of the exception.
- `String getMessage()`
    Returns a string with a message associated to the exception.
- `StackTraceElement[ ] getStackTrace()`
    Returns an object of the class `StackTraceElement[ ]` with the information about where the exception happened. Some of its methods are:
    - `String getClassName()`
    - `String getMethodName()`
    - `int getLineNumber()`
    - `String getFileName()`

The class `Exception` can be extended to create new exceptions.