
---
# Files

[Back to index](../README.md)

---
## Naming

- Files are a abstraction mechanism
	- Way of storing and reading information.
	- Simplification for the user.
- Whenever a process creates a file it assigns it a name
	- Other processes can access it through that name.
	- Name varies depending on the OS.

---
## Logical structure of files 

- OS only sees a unstructured sequence of bytes.
- Internal structure is imposed by user processes.

---
## File types

- **Regular files**
	- ASCII/text
	- Binaries
		- The internal structure is known by the process using it.
		- If that process is the OS the binary is called executable.
- **Directories**
	- Structure that the OS can understand.
- **Special files** (UNIX)

---
## File access

- **Sequential access**
	- Used in primitive OSs.
	- Information read/written sequentially byte by byte.
	- There is a pointer moving forward automatically.
- **Direct access**
	- Access is done directly through an address.
	- read/write operations must specify this address.
- **Indexed access**
	- Built over direct access
	- There is an index file that relates an index value to an address.