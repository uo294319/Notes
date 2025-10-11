
---
# 07 Object Oriented Programming

[Back to index](../README.md)

---

## Classes vs Objects

A **class** is an abstract scheme for storing some data and performing calculations with it.
- This data is a set of values called **attributes**.
- This operations (inner functions) are called **methods**.
- This structure remains the same for every object of a class
		Example -> Car ( Color, Weight, Dimensions )

A **object** is a particular of a class with its values set.
- The attributes have a particular value:
	Example -> My Car ( Red, 400 kg, Small )
	Example -> Other Car ( Blue, 1000 kg, Big )

## Class Definition

- Keyword `class` is used for defining a class.
- Every class needs a `__init__` method that is used for creating a class. Also called constructor method and cannot return a value.
- The `self` parameter is a reference to the object itself.
	- It allows accessing and modifying the atributes of the class

```python
class ExampleClass:
    def __init__(self, param = 1):
        self.value = val
```

## Object Definition

- The class attributes can also be accessed from outside the class.
	`objectName._class__attribute`

```python
example_object_1 = ExampleClass()
# __init__ method is called with param = None -> Now value = 1.

example_object_2 = ExampleClass(2)
# __init__ method is called with param = 2 -> Now value = 2.

value1 = example_object_1._ExampleClass__value
# Now value1 = 1

value2 = example_object_1._ExampleClass__value
# Now value1 = 2
```

## Class variables

- There also exists static attributes or class variables.
- They are a class property that is shared among all objects of that class.
	
```python
class ExampleClass:
	classCounter = 0
    def __init__(self, param = 1):
        self.value = val
        ExampleClass.classCounter += 1
      
example_object_1 = ExampleClass()
# Object value = 1 | ExampleClass.classCounter = 1

example_object_2 = ExampleClass(5)
# Object value = 5 | ExampleClass.classCounter = 2

example_object_3 = ExampleClass(46)
# Object value = 46 | ExampleClass.classCounter = 3
```

## Class methods
```python
class ExampleClass:

	# Constructor
	def __init__(self, arg = 0):
		self.value = arg
		
	# Some methods
	def setValue(self, arg = 0):
		self.value = arg
		
	def getValue(self):
		return self.value
		
obj = ExampleClass() # value = 0
obj.setValue(3) # value = 3
var = obj.getValue() # var = value = 3
```

## Class methods visibility
- Methods whose name start with `__` are hidden and cannot be accessed directly.
```python
class ExampleClass:
    def visible(self):
        print("visible")
    def __hidden(self):
        print("hidden")

obj = ExampleClass()
obj.visible() # Output -> "visible"
obj.__hidden() # Error
ExampleClass._Classy__hidden() # Output -> "hidden"
```
## Checking attributes existence

- Python allows objects of the same class to have a different set of attributes.
```python
class ExampleClass:
	def __init__(self, arg = 0):
		self.value1 = arg
	def setValue2(self, arg = 0):
		self.value2 = arg

example_object = ExampleClass() # Now only value1 exists.
print(example_object._ExampleClass__value2) # Error.

example_object.setValue2() # Now value2 is created.
print(example_object._ExampleClass__value2) # Output -> 0
```

- To check if a value exists we can use `hasattr(object, attribute)`
```python
example_object = ExampleClass() # Now only value1 exists.

print(hasattr(ExampleClass, "value1")) # Output -> True
print(hasattr(ExampleClass, "value2")) # Output -> False
```

## Built-in properties

- We can obtain a set of attributes of an object with `object.__dict__`.
- We can obtain the set of attributes and methods of a class with `class.__dict__`.
- We can obtain the name of a class by using `class.__name__`.
- We can obtain the set of direct super-classes by using `class.__bases__`.
- We can obtain the name of the module which contains the definition of a class or object by using `class.__module__` or `obj.__module__`.

> [!IMPORTANT]
> The module name `__main__` refers to the file currently being run.

```python
class ExampleClass:
	def __init__(self, arg = 0):
		self.value = arg

obj = ExampleClass()

print(ExampleClass.__dict__)
print(obj.__dict__) # Output -> {'value': 0}
```
