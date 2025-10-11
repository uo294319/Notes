
---
# 04 Conditionals

[Back to Java index](../README.md)

---

```java
// Single choice
if (condition) {
		// do if condition is true
} else 
        // do if condition is false
}

// Multiple choice
if (condition1) {
		// do if condition1 is true
} else if (condition2) {
		// do if condition1 is false and condition2 is true
} else {
		// do if both conditions are false
}

// Multiple choice
switch myVar {
		case value1:
				//do if myVar == value1
				break;
		case value2:
				//do if myVar == value2
				break;
		case value3:
				//do if myVar == value3
				break;
		default:
				// If no value is myVar's value this is executed
				break;
}
```