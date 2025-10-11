
---
# 06 Functions

[Back to index](../README.md)

---

## Definition

- We use `def` for defining a function.
- A function is a piece of recyclable code.
- Its main objective is to avoid repeated pieces of code.

```python
def myFunction():
	# Body
```


## Parameters

- Functions can receive variables from the external scope:
```python
def myFunction(param1 , param2):
	# Now we can use param1 and param2.
	# Body.
```

- Arguments can have a default value:
```python
def myFunction(param1 = 1 , param2 = "A"):
	# If we do not specify a value the default value will be used.
	# Body
```

- Arguments type can be specified:
```python
def myFunction(param1 : int , param2 : str):
	#Body
```
## Return and calling

#### Functions that perform an action

- They do not usually return a value.
- Sometimes we return `True`/`False` to indicate if the action has been performed correctly.

```python
# Example
def displayResults(results)
	print(results)
```
#### Functions that perform a calculation

- They perform some king of operation and return the results.
```python
def calculateResults():
	# Calculating
	return results

myVariable = calculateResults()
# Now myVariable contains the results
```

- The return type can be specified:
```python
def getTwo() -> int:
	return 2
```