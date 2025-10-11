
---
# 04 Control Structures (if-else / while)

[Back to index](../README.md)

---

## Conditionals

```python
if condition1:
		# code executed if:
        #     condition1 == True
elif condition2:
		# code executed if:
        #     condition1 == False
        #     condition2 == True
else:
		# code executed if:
        #     condition1 == False
        #     condition2 == False
```

## Repetitive (while)

```python
# General
while condition:
		# code to be executed while condition == True
        # The tabulation or indentation is really important

# This line is NOT inside the while
```

```python
# Using an ascending control variable (n)
n = 0
while n < 10:
		# Code
		n += 1 # The control variable is incremented
```
```python
# Using an descending control variable (n)
n = 10
while n > 0:
		# Code
		n -= 1 # The control variable is decremented
```

```python
# Using a flag
flag = True
while flag:
		# code
		flag = False # Until some circumstance we make the loop stop
```

We can also use `break` to exit a loop

We can use `continue` to return to the start of the loop 

At the terminal, if a loop turns to be infinite we stop it with `ctrl + C`