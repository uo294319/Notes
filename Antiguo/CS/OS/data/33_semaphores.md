
---
# Semaphores

[Back to index](../README.md)

---

## Definition of semaphore

- Processes cooperates through signals.
	- Processes wait until a signal is received
- Special variables called semaphores (`s`) are used.
	- To send a signal `V(s)` or `signal(s)` (releases a process).
	- To receive a signal `P(s)` or `wait(s)` (blocks a process).
- Implementation:
	- Semaphores are integer variables initialized with a non-negative value.
	- Operation `V` increases the value of a semaphore.
	- Operation `P` decreases the value of a semaphore.
- Types:
	- General or counting (any value)
	- Binary or mutex (Only `0` and `1`)

---
## Solution to the mutual exclusion problem

### Simple Section
```C
semaphore mutex = 1 // mutex initial value is always 0

P(mutex); // entry section
// CRITICAL SECTION
V(mutex); // exit section
```
### Sections inside if  
```C
P(mutex);
if(condition) { // CRITICAL SECTION (in the condition)
	V(mutex);
	// code
}
else V(mutex); 
```
### Sections inside while
```C
P(mutex);
while(condition) {// CRITICAL SECTION (in the condition)
	V(mutex);
	// code
	P(mutex);
}
else V(mutex); 
```
### Sections inside return
```C
P(mutex); // entry section
aux_var = ...;// CRITICAL SECTION
V(mutex); // exit section
return aux_var;
```

---
## Solution to synchronization problems

- P2 starts when P1 ends.
```C
semaphore sync = 0 // initial value 0

void P1() {
	// code
	V(sync);
}

void P2() {
	// code
	P(sync);
}
```

---
## The producers/consumers problem

- Common problem in communications.
- There are two threads/processes:
	- **Producer**. Continuously generates data to a FIFO.
	- **Consumer**. Continuously consumes data from the FIFO.

---