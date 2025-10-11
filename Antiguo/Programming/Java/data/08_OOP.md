
---
# 08 Classes & Objects

[Back to Java index](../README.md)

---

## Classes vs Objects

- A class is a common structure that forms a non-primitive datatype.
- It has some atributes or properties and some methods or behaviours. They can be either static or not.
    - Static ones have a common value for all instances of a class (its objects).
    - Non-Static (or Instance) ones can have a different value.
- A object is a specific instance of that classs

```java
public myClass {
    // Instance atributes (belong to the object/instance)
    // Instance methods (Constructors, getters, setters ...)

    // Static atributes   (belong to the class, is the same for every object)
    // Static methods
}

// Object of the previous class
myClass myObject = myClass()
```

## Modifiers

| Modifier      | Class | Package | Subclass | World |
| --------------| ------| --------| ---------| ------|
| `public`      | Yes   | Yes     | Yes      | Yes   |
| `protected`   | Yes   | Yes     | Yes      | No    |
| _No modifier_ | Yes   | Yes     | No       | No    |
| `private`     | Yes   | No      | No       | No    |

## Atributes

```java
// Static atributes (the same for every object)
public static final type  myVar = value;    // Do not changes
public static type myVar = value;           // Changes

// Object atributes
private type myVar1;  // Only accesible inside the class (correct way)
private type final myVar3;  //Can only be modified by the constructor
```

## Constructors

```java
**// default constructor (not always necessary)**
// Atributed will be null or 0 depending on the type
// If there's no constructor this one will be provided
public myClass() {}

**// Parametrized**
// (could use any number of variables)
public myClass(type myVar1, type myVar2) {
    this.myVar1 = myVar1;
    this.myVar2 = myVar2;
}
// Is a good practice to pass this variables throught the setters
public myClass(type myVar1, type myVar2) {
    this.setMyVar1(myVar1);
    this.setMyVar2(myVar2);
}

**// Copy constructor**
// If type is not primitive we should asure that no memory adress is provided
public myClass(myClass another) {
    this.myVar1 = another.getMyVar1();
    this.myVar2 = another.getMyVar2();
}
```

## Getters / Setters

```java
**// Getter**
public type getMyVar1() {
    return this.myVar1;
}
// If type is not primitive we should asure that no memory adress is provided
public type getMyVar2() {
    return new type(myVar2)  // Only works if there's a copy constructor
}

// Setter
public void setMyVar1(type newVar1) {
    if(condition) {
        throw exception(message);  // Particular exception must be shown
    }
    // IllegalArgumentException  -  NullPointerException
    this.myVar1 = newVar1;
}

```

## Other Methods

```java
// Normal method implementation.
public type myMethod(type sth) {body}

// Method with a variable number of arguments
public type myMethod(type... array) {body}
// Same type parameters. Treated like an array. Must be the last parameter
```

## `This` keyword

```java
// this refers to the class itsef.
this()            // calls the no-parameter default constructor
this(myVar1)      // calls a parametrized constructor
this.myVar        // access myVar1 in this class
this.myMethod()   // calls myMethod() in this class

// Cannot be called in a static method.
// If used inside  a constructor it must be at the very first line.
```
