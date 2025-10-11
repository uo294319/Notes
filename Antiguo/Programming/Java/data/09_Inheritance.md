
---
# 09 Inheritance

[Back to Java index](../README.md)

---
## Composition vs Inheritance

- **Composition** is when a class has another one.
	- One of its attributes is of the other class type.
- **Inheritance** is when a class is a more specific type of the first one.
	- The class **extends** the first one.
## Intro

```java
// Subclass is a child of the parent class superclass.
public subclass extends superclass {body}
```

- Subclasses inheritate all methods and atributes from the superclass except the constructors.
- Only the non-private ones are accesible.
- Java only allows simple inheritation (only one superclass)
- If no superclass is indicated by default it will be extended from `Object` java class.
    - Its methods: `clone` , `equals` , `getClass` , `toString`
## Super

```java
// super is used in child classes to call the parent one.
super()            // calls the no-parameter default constructor of the superclass
super(myVar1)      // calls the default constructor of the superclass
super.myVar        // access myVar1 in the superclass
super.myMethod()   // calls myMethod() in the superclass

// super can only be used inside constructors at the very first line.
// by default all constructors calls super() at the first line
```
## Final

```java
public final type sth;
// Final attribute. Attribute can only be modified by the constructor.

public final myClass {body}
// Final class. Class cannot be extended.

public final type myMethod(type sth) {body}
// Final method. Method cannot be overridden in subclases.
```
## Override

```java
// Indicates the following method is replacing the one in the superclass
@Override
public void toString() {body}
```