
---
# 06 File I/O

[Back to index](../README.md)

---

```python
file = open("filename.txt", "r")
# "r" for read
# "w" for write (removes and creates file)
# "a" for append

file.read()       # Returns the whole file.
file.read(i)      # Returns the first i characters of the file.
file.readline()   # Returns a line and next call reads the next one.
file.readlines()  # Returns an array with all lines one by one.
file.write(sth)   # Writes something into the file.

file.close()      # Always close the file after opening it.
```