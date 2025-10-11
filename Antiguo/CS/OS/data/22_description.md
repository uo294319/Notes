
---
# Processes description

[Back to index](../README.md)

---
## Processes Basics
### Definition

- A process is an instance of a program.
- Its different parts are stored in the main memory.
	- **Context** (Some information needed by the OS)
	- **Data**
	- **Program Code**
	- **Stack**
### Creation

- It should be created in the main memory.
- Two ways:
	- Loading program from the secondary memory.
	- Through clonation of another pre-existing process.

---
##  Control Structures of the OS

### Process Control Block (PCB)
- PCB is a OS data structure with all the critical information about a process.
- Every existing process have a PCB.
- Each OS implements the PCB differently.
- PCBs are organized in the Processes Table.
- Contains:
	- **Identification**
		- Process ID (PID). Unique integer that identifies a process. 
		- Parent ID. PID of the process that created this process.
		- User ID (UID). The ID of the process owner. 
	- **State information**
		- Contents of the CPU registers when not running.
	- **Control information**
		- Planning (priority) and status.
		- Communication between processes.
		- Privileges of the process.
		- Memory addresses of code, data and stack.
		- Use and ownership of resources
### Processes Table
- OS must keep up-to-date information about processes status.
- The processes table is an indexed vector with the processes IDs (PID).
- Contains pointers to the PCBs o the PCBs themselves.
- Always resides in the main memory.

---
