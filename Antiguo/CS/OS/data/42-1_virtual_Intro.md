
---
# Virtual Memory Management Introduction

[Back to index](../README.md)

---
## Problem with Real Memory

- With real memory scheme:
	- Processes must be completely loaded in MM.
	- We do not need the whole program in MM.
- To partially load processes have some advantages:
	- Allowance to run programs greater in size than MM.
	- More programs can be in MM.
		- Increases multiprogramming level.
		- Switching operations are less expensive.

---
## Presenting Virtual Memory

- Only used parts of the process are kept in MM.
	- The rest is kept in secondary storage.
- Is transparent to the programmer.
- Requires hardware support: Memory Management Unit (MMU)

---