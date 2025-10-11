
---
# Introduction to Processes Coordination

[Back to index](../README.md)

---
## Principles of concurrency

- **Concurrent processes**: interleave or overlap its execution.
- **Parallel processes**: overlap its execution.
- **Concurrency and parallelism**
	- Multi-programming (mono-processor)
		- No real parallelism. Processes interleave.
	- Multi-processing and distributed (several CPUs)
		- Real parallelism. Processes interleave and overlap.
- **Concurrency Problems**
	- Shared global resources.
	- Processes synchronization.
	- Inefficient resource assignment.
	- Difficult programming error identification (not repeatable scenarios)

---
## Classification of processes interaction

1. Contest among processes
	- Independent processes trying to access same resource.
	- OS is responsible of resources assignment.
	- *Mutual Exclusion* problem.
2. Sharing cooperation among processes
	- Processes cooperate to share resources without knowing each others.
	- Programmer is responsible of controlling cooperation.
		- OS provides system calls.
	- *Mutual Exclusion* problem.
3. Communication cooperation among processes
	- Processes send messages (synchronize) between them.
	- Programmer is responsible of communication.
		- OS provides services for sending and receiving.
	- No *Mutual Exclusion* problem.

---
## The problem of mutual exclusion

1. Programmer writes the code as if there was no problem
2. Programmer must identify the **critical sections**
	- Pieces of code accessing to shared resources
	- Programmer must:
		- Grant exclusive accesses to the process to the resource.
		- Forbid any other process to use that resource.
	- This critical sections must be mutually exclusive in time.
3. Add specific code to all critical sections
	- Entry section (Before a critical section).
		- Blocks the resource (forbidden to other processes).
	- Exit section (After a critical section).
		- Release the resource (accessible to other processes).

---