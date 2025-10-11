
---
# Exceptions

[Back to index](../README.md)

---

## Simple try-except

````python
try:
	# Code to safely execute.
	# It will be executed until an exception is raised.
except:
	# Executed if any exception is raised.
````

## Multiple try-except

````python
try:
	# Code.
except ErrorType2:
	# Executed if an exception of the type ErrorType2 is raised.
except (ErrorType1, ErrorType1):
	# Multiple except with different exceptions can follow a try.
	# Multiple types of exceptions can be specified.
````

## Raise keyword

````python
raise Exception
# Raises an exception of the specified type.
````

````python
try:
	# Code.
except:
	raise
	# Inside an except it re-raises the handled exception.
````

## Assert keyword

````python
assert expresion
# Raises a AssertionError if the expresion is None, 0, false, "" or []
````

## Commonly used exceptions

- `BaseException`
	- `SystemExit`
	- `KeyboardInterrupt`
	- `Exception` (general one)
		- `AssertionError`: Always raised by a `assert`.
		- `ValueError`: Invalid value for a method.
		- `LookupError`
			- `IndexError`: Try to access non-existent element in a sequence.
			- `KeyError`: Try to access non-existent key of a dictionary.
		- `ArithmeticError`: Invalid domain for a arithmetic operation
			- `ZeroDivisionErrror`: Try to divide by `0`.
			- `OverflowError`: Number to big to be stored.
		- `MemoryError`: Lack of free memory.
		- `ImportError`: Error importing libraries.