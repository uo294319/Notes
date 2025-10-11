
---
# Factory Patterns

[Back to index](../README.md)

1. [Description](#description)
2. [Factory Method](#factory-method)
3. [Simple Factory](#simple-factory)
4. [Abstract Factory](#abstract-factory)
5. [Summary](#summary)

---

## Description

The objective is to encapsulate the instantiation of classes of the same type by using a creator class instead of direct instantiation.

> [!WARNING]
> Note that the creator class can contain most of the program logic.

---
## Factory Method

### Characteristics

- We implement a `Creator` class
	- Contains the **abstract** Factory Method (`createProduct()`).
	- Should have no logic **FOR CREATION**.
	- Can be an abstract class.
- We implement a specific creators
	- One for each concrete product.
	- Contains all the logic for that product creation.
	- Contains a specific implementation of `createProduct()`.

### UML

```mermaid
classDiagram
direction LR

Creator --|> Creator_A
Creator --|> Creator_B

Creator_A --> Product_A :  creates 
Creator_B --> Product_B :  creates 

Product_A --|> Product
Product_B --|> Product

class Product {
	<< I >>
}

class Product_A {
	<< C >>
	~Product_A()
}

class Product_B {
	<< C >>
	~Product_B()
}

class Creator {
	<< C >>
	+ createProduct() Product*
	+ operation() void
}

class Creator_A {
	<< C >>
	+createA() Product_A
}

class Creator_B {
	<< C >>
	+createB() Product_B
}

```

### Use

```java
public class Main {
	public void main(String[] args) {
		Creator cA = new Creator_A();
		
		// If we want to use the creator
		cA.operation();

		// If we want to use a product
		cA.createProduct();
	}
}

public class Creator {
	public abstract Product createProduct();
	
	public void operation() {
		Product p = createProduct();
		// Do something with p
	}
}

public class Creator_A extends Creator{
	public Product createProduct() {
		return new Product_A()
	}
}
```

---
## Simple Factory

### Characteristics

- Similar to Factory Method.
- Has no specific creators but a general one.

### UML

```mermaid
classDiagram
direction LR

Creator .. Product
Product <|-- Product_A
Product <|-- Product_B

class Product {
	<< I >>
	+makeProduct() Product$
}

class Product_A {
	<< C >>
	~Product_A()
}

class Product_B {
	<< C >>
	~Product_B()
}

class Creator {
	<< C >>
	+ operation() void*
}
```

### Code

```java
abstract class Product {
	static Product makeProduct(char type) {
		switch(type)
		{
			case 'A' -> return new Product_A();
			case 'B' -> return new Product_B();
		}
	}
}

class Product_A extends Product { ... }
class Product_B extends Product { ... }

class Creator {
	public void operation() {
		Product pA = Product.CreateProduct('A');
		Product pB = Product.CreateProduct('B');
	}
}
```

---
## Abstract Factory
### Characteristics

- Similar to the Factory Method but with families of objects.
- We implement creators for groups of objects with certain restrictions.

### UML

```mermaid
classDiagram
direction TB

AbstractFactory <|-- ConcreteFactory1
AbstractFactory <|-- ConcreteFactory2

ConcreteFactory1 --> ConcreteProductA1
ConcreteFactory1 --> ConcreteProductB1

ConcreteFactory2 --> ConcreteProductA2
ConcreteFactory2 --> ConcreteProductB2

ConcreteProductA1 --|> AbstractProductA
ConcreteProductA2 --|> AbstractProductA

ConcreteProductB1 --|> AbstractProductB
ConcreteProductB2 --|> AbstractProductB

class AbstractFactory {
	<< I >>
	+ createProductA() ProductA *
	+ createProductB() ProductB *
}

class ConcreteFactory1 {
	<< C >>
	+ createProductA() ProductA
	+ createProductB() ProductB
}

class ConcreteFactory2 {
	<< C >>
	+ createProductA() ProductA
	+ createProductB() ProductB
}

class AbstractProductA {
	<< I >>
}

class ConcreteProductA1 {
	<< C >>
}

class ConcreteProductA2 {
	<< C >>
}

class AbstractProductB {
	<< I >>
}

class ConcreteProductB1 {
	<< C >>
}

class ConcreteProductB2 {
	<< C >>
}
```

---
## Summary

- **Factory Method**
	- Encapsulate object creation logic.
	- Easily extensible code.
	- Addition without existing code modification.
- **Simple Factory**
	- Encapsulate object creation logic.
	- Easy hierarchy of objects.
	- Addition with existing code modification.
- **Abstract Factory**
	- Families of objects.
	- Restrictions present.