
---
# 10 Polymorphism

[Back to Java index](../README.md)

---
## instanceof operator
```java
// Having Dog and Cat extend an Animal
Animal myAnimal = new Dog();
myAnimal instanceof Dog       // >>> True
myAnimal instanceof Animal    // >>> True
myAnimal instanceof Cat       // >>> False
```
## Downcasting vs Upcasting
```java
// Having Dog and Cat extend an Animal
// Upcasting is when a child class is identified as its parent one
// Useful when creating methods that are the same for all childs of a class
// Can only use methods that are defined in the superclass
// but the subclass implementation will be executed instead
Animal myAnimal1 = new Dog();
Animal myAnimal2 = new Cat();

// To access methods that are not defined in the superclass upcasting is needed
Dog myDog = (Dog) myAnimal1;
Cat myCat = (Cat) myAnimal2;

```
## Abstract keyword
```java
// Aplied to classes
// They cannot be instantiated, only used for inheritation.
public abstract class myClass {body}

// Aplied to methods
// They have no implementation. It should be given in subclasses.
public abstract type myMethod(params);
```
## Interfaces
```java
public interface myInterface
{
    // All atributes declared in an interface are static and final
    private type myAtribute;

    // All methods declared in a interface are abstract
    public type myMethod();
    
    // A default implementation can be provided
    public type setMyAtribute()
    {
        throw new UnsupportedOperationException();
    }
}

// Interface usage.
// A class can implement more than one interface.
// All non-abstract classes must implement all interface's methods
public class myClass implements myInterface {body}
```