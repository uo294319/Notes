
---
# 01 Basics

[Back to index](../README.md)

---

### Basic operations
| Name | Symbol |
| ---- | ---- |
| Parenthesis | `( )` |
| Power | `^` |
| Addition | `+` |
| Substraction | `-` |
| Multiplication | `*` |
| Regular division | `/` |
| Left division | `\` |
## Variables

```matlab
% Simple variable
var = 1;

% Symbolic variables
syms x y;
x + 3*y;
```
## Predefined Variables
| Variable | Description |
| ---- | ---- |
| `ans` | Last result not assigned to a variable. |
| `pi` | Value of pi. |
| `i` -  `j` | Imaginary units. |
| `+inf` -  `-inf` | Infinity. |
| `NaN` | Not a number. |
## Predefined functions
| Function | Description |
| ---- | ---- |
| `abs(x)` | Absolute value |
| `exp(x)` | Exponential `e^x` |
| `log(x)` | Natural logarithm of `x` |
| `log2(x)` | Base 2 logarithm of `x` |
| `log10(x)` | Base 10 logarithm of `x` |
| `sqrt(x)` | Square root of `x` |
| `cbrt(X)` | Cube root of `x` |
| `nthroot(x, n)` | n-th root of `x` |
| `sin(x)` | Sine of `x` |
| `cos(x)` | Cosine of `x` |
| `tan(x)` | Tangent of `x` |
| `asin(x)` | Inverse sine of `x` |
| `acos(x)` | Inverse cosine of `x` |
| `atan(x)` | Inverse tangent of `x` |
## Creating functions
```matlab
% Symbolic function
>> syms x y
>> f(x y) = x + y^2;
>> 
>> f(2 1)
ans = 
	3
	
% Anonimus function
>> f = @(x y) x + y^2;
>> f(2 1)
ans = 
	3

% Anonimus -> Symbolic
>> syms x y
>> f_simbolic(x y) = f_anonimus(x y)

% Symbolic -> Anonimus
>> f_anonimus = f_simbolic(x y)
```
## Some basic commands
| Command | Description |
| ---- | ---- |
| `whos` | Displays all variables in current session. |
| `clear` | Remove all variables from current session. |
| `date` | Current date. |
| `disp( A )` | Displays contents of A in the console |
## Use of semicolons

In a Matlab script each operation displays its result in the console. To prevent the console from being illegible, each script line ending with a semicolon will not be displayed when executed.

## Ploting graphs

```matlab
% Plots the points (1,1), (2,2), (3,4), (4,3)
% and then connects them. 
>> plot([1 2 3 4],[1 2 4 3])

%% Plots a function f
% where r is the displayed x range. Example: [-3, 3]
>> fplot(f, r)
```