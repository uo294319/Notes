
---
# Virtual Memory Implementation
[Back to index](../README.md)

---
## Introduction
There are several ways of implementing Virtual Memory:
- **Paging** (Only one explained here)
- **Segmentation**
- **Paged Segmentation**

---
## Paging
### Organization of the Memory
- Process is divided into fixed-size blocks called pages.
- MM is divided into fixed-size blocks called frames.
- Pages and frames are of the same size.
### Data Structures
- **Pages table**
	- One per process.
	- Pointed by a register in MMU
	- Contains:
		- Page number.
		- Protection bits.
		- Modified bit (1 if modified).
		- Present bit (1 if in MM).
		- Reference bit  (1 if referenced recently).
- **File map table**
	- Address of the processes in secondary storage.
- **Frames table** (as in simple paging)
	- Only one for whole system.
	- Has an entry for each frame (assigned/free, page number, PID)
### Address translation
1. Divide the virtual address into page number and offset.
2. Access the page table of the process.
	- Try to translate the page number to a frame number.
	- If present bit is set to 0 throw a Page Fault Exception.
		1. OS takes control and moves the process to blocked state.
		2. Locate page in secondary memory.
		3. Loads the page to MM (I/O operation).
		4. Updates the page table and moves the process to ready state.
		5. Restarts the execution of the instruction.
3. Access the MM with the physical address.
	- physical address = frame number + offset.
	- Locate the frame number and the offset inside it.
---