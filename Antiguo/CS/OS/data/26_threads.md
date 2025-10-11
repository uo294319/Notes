
---
# Threads

[Back to index](../README.md)

---

## Introduction

- Modern OS manages differently:
	- Process (Resource owner unit, do not run)
	- Thread (minimal scheduling running unit)
- Processes own threads.
- Multithread OS allows processes to have several threads.

---
## Composition in Main Memory

- **Processes**
	- Are stored at main memory.
	- Formed by:
		- Code
		- Data
		- At least one running thread (main thread)
	- Do never execute code.
		- PCB without some parts (running state, context, etc).
- **Threads**
	- Formed by:
		- Thread Control Block (TCB) is a *mini PCB*. 
			- Contains the thread state and context.
		- Stack is unique to each thread.
	- Accesses memory and resources that belong to their process.
	- Resources are shared between threads of the same process.

---
## Process and Thread Creation

- Processes are created by the OS Long-Term Scheduler (LTS)
	- Loads runnable file from secondary memory to the main memory
	- Creates a process and its main thread.
		- Process (code, data and PCB)
		- Thread (TCB and stack)
- Extra threads must be created by the programmer.
	- Requires a system call to the OS.
	- Fast and efficient creation.
	- Threads share code and global data of the process.
	- Usually, each thread runs a piece of the program.

---
## Process and Thread Management

- STS works with threads.
	- CPU is assigned to a thread.
	- Threads are the only ones with states.
	- Context of threads is saved/restored.
- MTS works with processes.
	- Whole processes (all its threads) are suspended/activated.

---
## Process and Thread Ending

- Threads can end independently of other threads.
- A process ends when all its threads end.
	- Sometimes, the rest of threads are ended when the main thread ends.
- The memory is freed when the whole process ends.

---
## Benefits of Threads

- Easier to create a new thread than a whole process.
- Easier to end a existing thread than a whole process.
- Easier to change the state of a thread than that of a whole process.
- Threads of the same process can communicate between them.

---