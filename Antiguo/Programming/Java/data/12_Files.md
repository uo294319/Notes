
---
# 12 Files

[Back to Java index](../README.md)

---
## Introduction
Here we are going to see how to obtain information from outside the program and how to store it outside of it. When doing this, we shoud always treat the `IOException`  and the `FileNotFoundException` that may be trown.

For doing this we use a stream, that can be classified in:
- Character Stream. Used when we want something human-readable.
- Byte Stream. Used when we just want to transfer information.

We will use the following classes:
- For reading bytes:
    - `FileInputStream(File file)`
    - `FileOutputStream(File file)`
- For reading from text file:
    - `Scanner`
    - `Formatter`
- For reading objects (serialization):
    - `ObjectInputStream(File file)`
    - `ObjectOutputStream(File file)`
## FileInputStream & FileOutputStream
```java
FIleInputStream fileIn = null;
FIleOutputStream fileOut = null;

try {
    //Can be a file of any extension
    fileIn = new FileInputStream("fileIn.txt");
    fileOut = new FIleOutputStream("fileOut.txt");
    int bytecode;
    
    do
    {
        // Reads a byte from the file
        // -1 if there is no bytes left
        int bytecode = fileIn.read();
        if(bytecode != -1)
            // Write a byte to the file
            fileOut.write(bytecode);
    } while(bytecode != -1);
    
} catch (IOException e){
    System.out.println(e)
} finally {
        // Cerramos el archivo
        if(fileIn != null) fileIn.close();
}
```
## Scanner & Formatter
When reading from a file we divide its content in tokens (a piece of information), each of them separate by a delimiter.
```java
     Scanner input = null;
     try {
        input = new Scanner(new FileInputStream("fileToRead.txt"));
        // A new delimiter for tokens can be set
        // By default its "\r\n|\t| "
        input.useDelimiter(",|\r\n")
        while(in.hasNext())
            // next() returns a string token
            // nextInt() returns a int token
            // nextFloat() returns a float token
            // nextLine() returns a whole line
            System.out.println(input.next())
    } catch (IOException e) {
        throw new IOException(e);
    } finally {
        if (input != null) input.close();
    }
}
```

```java
Formatter output = null;
try {
    output = new Formatter("fileToWrite.txt");
    // Works as printf()
    output.format("Hello World\n");
} catch (IOException e) {
    System.out.println("IOException : " + e);
} finally {
    if(output != null) output.close();
}
```
## Serialization
Is the conversion of a whole object of a determined class to a byte file. For an object to be able to be serialized it needs its class to extend the interface `Serializable`. For this we will use the `ObjectOutputStream` method `writeObject()` and the `ObjectInputStream` method `readObject()`

```java
Object serializableOut = new Object();
ObjectOutputStream fileOut = null

try {
    fileOut = new ObjectOutputString(FileOutputStream("myClassOut.ser"));
    fileOut.writeObject(serializableOut)
} catch (IOException e){
    System.out.println(e)
} finally {
    // Cerramos el archivo
    if(fileOut != null) fileOut.close();
}
```

```java
Object serializableIn;
ObjectInputStream fileIn = null

try {
    fileIn = new ObjectInputString(FileInputStream("myClassOut.ser"));
    
   // To use another class you need to downcast
   serializableIn = fileOut.readObject();
} catch (IOException e){
   System.out.println(e)
} finally {
    // Cerramos el archivo
    if(fileIn != null) fileIn.close();
}
```