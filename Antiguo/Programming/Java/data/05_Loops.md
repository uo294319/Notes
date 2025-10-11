
---
# 05 Loops

[Back to Java index](../README.md)

---

## While loop

```java
// First evaluates the condition and latter runs the body
while (condition) {
		//body
}

// First runs the body and latter evaluates the condition
do {
		//body
} while (condition);

/*
* Diferent ways of controling execution can be implemented
* int a=0        -->  a++      --> i is called a control variable
* boolean a=true -->  a=false  -->  a is called a flag
*/
```

- `continue` Jumps back to the loop condition check
- `break` Force to finish the loop

## For loop

```java
// Normal for loop
for(type Var = value  ;  cond  ;  convergence) {body}

// Example
for(int i = 0 ; i < 5 ; i++) {
		//body (i = 0, 1, 2, 3, 4)
}

// for loop to iterate over an array (or List)
for (type element : list) {body}

// Example
int[] numbers = {13, 34, 25, 12 , 4}
int currentLargest = numbers[0];
for (int number : numbers) {
		if (number > currentLargest)
					currentLargest = number;

System.out.println(currentLargest)  // prints largest number in the list
```