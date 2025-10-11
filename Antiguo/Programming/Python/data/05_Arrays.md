
---
# 05 Arrays and `for` loop

[Back to index](../README.md)

---

## Arrays creation

```python
# Empty array
myArr = []
```
```python
# Simple array of integers.
# Each element has a index starting from 0 (top left).
myArr = [1, 2, 3, 4, 5, 6]
# myArray[0]     -> 1
# myArray[2]     -> 3
# myArray[-1]    -> 6          It can be accessed from the bottom with negative values.
# myArray[1:3]   -> [2, 3]     A range can be accessed (index 1 is included but 3 is not).
# myArray[1:6:2] -> [2, 4, 6]  Access a range jumping 2 elements.
```
```python
# Matrix
# Technically is an array in wich each element is another array.
myArr = [[1, 2], [3, 4], [5, 6]]
# myArr[1]    -> [3, 4]
# myArr[1][1] -> 4     
```
## Arrays methods

```python
  myArr = [ 1, 2, 3         ]

myArr.append(4)
# myArr = [ 1, 2, 3, 4      ]     Add to the end a single item.

myArr.extend([5, 6])
# myArr = [ 1, 2, 3, 4, 5, 6]     Add to the end multiple items in a list.

myArr.insert(29, 0)
# myArr = [29, 2, 3, 4, 5, 6]     Insert an item at given position.

myArr.pop(2)
# myArr = [29, 2,    4, 5, 6]     Remove given index from the list and returns it.

myArr.remove(5)
# myArr = [29, 2,    4,    6]     Remove given value from the list.

sorted(myArr)
# myArr = [2, 4, 6, 29]           Array is now sorted.
```

## For

```python
for i in Array:
		# code
		# The variable i will be obtaining each value of the Array one by one.
```

```python
range(num0, num1, k)
# Returns an array with num0 as first number
# Then it will add k until it is greater or equal to num1
# By default  num0 = 0  and  k = 1

range(5)           # 0, 1, 2, 3, 4
range(2, 6)        # 2, 3, 4, 5
range(0, 10, 2)    # 0, 2, 4, 6, 8
```

```python
# Usually used together
for i in range(10)
	# code
	# i will be first 0, then 1, 2, ... , until 9
```

## Using arrays to formatting strings

```python
date = "2022/12/31"

# Create a list by splitting a string by given character
date_list = date.split("/")
# date_list = ['2022', '12', '31']

# Create a string by joinning a list with given character
date_hyphen = "-".join(date_list)
# date_hyphen = '2022-12-31'
```