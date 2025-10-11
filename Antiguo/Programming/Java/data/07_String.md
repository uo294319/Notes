
---
# 07 String

[Back to Java index](../README.md)

---

`String` class is inmutable

```java
String myString1 = new String("Hello World");
String myString2 = "Hello World";
```

`StringBuffer` class is mutable

```java
StringBuffer mySB = new StringBuffer();
```

---

```java
String myStr = "Hello World";

//lenth() lleva parentesis
for(int i=0; i<myStr.lenth(); i++) {
		char myChar = myStr.charAt(i);
		System.out.println(myChar);
}
```