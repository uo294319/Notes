
---
# Singleton

[Back to index](../README.md)

---

## Description

Guaranties only one instance of a class and provide global access to it.
Uses lazy instance initialization.

## Characteristics

- Static variable: `instance`.
- Private constructor.
- Static function `getInstance()`

## UML

```mermaid
classDiagram
class Singleton {
	- Singleton instance $
	- Singleton()
	+ getInstance() Singleton $
}
```
## Code

```java
public class Singleton { 

	private Singleton() { ... }
	
	private static Singleton instance = null;
	
	public static Singleton getInstance() {
		if (instance == null)
			instance = new Singleton();
		return instance;
	}
}
```