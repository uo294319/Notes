
---
# 02 Vectors & Matrices

[Back to index](../README.md)

---

## Vectors
### Creation

```matlab
>> V = [1 2 3]
V = 
	1    2    3
    
>> V = [1, 2, 3]
V = 
	1    2    3
	
% initial : increment : end

>> V = [1 : 2 : 10]
V = 
	1    3    5    7    9

>> V = [11 : -2 : 3]
V = 
	11    9    7    5    3

% Increment by default is 1 or -1

>> V = [1 : 5]
V = 
	1    2    3    4    5

% We can also use linspace(a, b, n)
% Creates a vector with `n` elements equally spaced
% between `a` and `b`. 

>> linspace(2, 8, 4)
ans = 
	2    4    6    8

>> linspace(2, 3, 5)
ans = 
	2.00    2.25    2.50    2.75    3.00
```

### Access

```matlab
>> V = [3, 1, 2, 5, 4];

>> V (2)
ans =
	1

>> V ([3 5 1])
ans =
	2    4    3

>> V ([1 : 2 : 5])
ans =
	3    2    4

% end keyword is substituted by the last index of the vector

>> V(end)
ans =
	4

>> V(end - 2)
ans =
	2

>> V ([3 : 1 : end])
ans =
	2    5    4
```

### Some functions

| Function | Description |
| ---- | ---- |
| `length(V)` | Returns number of elements of a vector. |
| `sum(V)` | Returns the sum of all elements of a vector. |
| `prod(V)` | Returns the product of all elements of a vector. |
| `max(V)` | Returns the maximum element of a vector. |
| `min(V)` | Returns the minimum element of a vector |

## Matrix
### Creation

```matlab
>> A = [0 1 2; 2 3 5; 3 4 6]
A =
	0    1    2
	2    3    5
	3    4    6

>> B = [6, 7; 7, 8; 8, 9]
B =
	6    7
	7    8
	8    9

% Matrixes can be concatenated

>> C = [A B]
C =
	0    1    2    6    7
	2    3    5    7    8
	3    4    6    8    9
```

| Function | Description |
| ---- | ---- |
| `ones (n , m)` | Creates a `n x m `matrix full of `1`.<br>If `m` is not specified it will have the value of `n`. |
| `zeros (n , m)` | Creates a `n x m` matrix full of `0`.<br>If `m` is not specified it will have the value of `n`. |
| `eye(n , m)` | Creates a `n x m` matrix with `1` in the main diagonal and `0` elsewhere.<br>If `m` is not specified it will have the value of `n`. |
| `diag(v)` | Creates a matrix with the vector `v` as main diagonal and `0` elsewhere. |
### Access

```matlab
>> A = [0 1 2; 3 4 5; 6 7 8];

>> A (2 , 3)
ans =
	5

>> A ([1 2] , 1)
ans =
	0
	3

>> A (1 , 2:3)
ans =
	1    2

% : can be used to specify the whole row/columm

>> A (1 , :)
ans =
	0    1    2
```


### Operations

| Symbol | Description |
| ---- | ---- |
| `A + B` | Matrix addition.  |
| `A - B` | Matrix subtraction.  |
| `A * B` | Standard matrix multiplication. |
| `A .* B` | Elementwise multiplication. |
| `A / B` | Equivalent to `A * inv(B)`. |
| `A ./ B` | Elementwise right division. |
| `A \ B` | Equivalent to `inv(A) * B`. |
| `A .\ B` | Elementwise left division. |
| `A .^ B` | Elementwise power. |

### Some Functions

| Function | Description |
| ---- | ---- |
| `size(A)` | Returns a vector with the dimensions of matrix `A`. |
| `sum(A)` | Returns a vector containing the sum of each column of a matrix. |
| `prod(A)` | Returns a vector containing the product of each column of a matrix. |
| `max(A)` | Returns a vector containing the maximun of each column of a matrix. |
| `min(A)` | Returns a vector containing the minimun of each column of a matrix. |
| `inv(A)` - `A.'` | Returns the inverse of A. |
