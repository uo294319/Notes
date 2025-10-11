
---
# Hardware solutions to mutual exclusion

[Back to index](../README.md)

---
## Disabling Interruptions

- In mono-processor computer processes are interleaved
	- Processes are only disrupted because of interruptions.
	- Disable interruptions during critical sections to solve *Mutual Exclusion*.
- Cons:
	- OS cannot get to the CPU.
	- Processes interleaving rate is degraded. 
	- Useless for multicore architectures.

---
## Special Machine Instructions

- In multicore computers, processors are granted exclusive access to memory.
	- Create special machine instructions to access memory in a single cycle.
	- This makes imposible the interference with other instructions.

### Test&Set
```C
boolean Test&Set(boolean &origin) {
	boolean aux = origin; //memory position
	if (!origin) origin = true;
	return aux;
}

// >>> USAGE <<<
while( Test&Set(&lock) ) do {nothing}; // Entry section
// CRITICAL SECTION
lock = false; // Exit section
```

- Function cannot be disrupted (atomically executed)
- CPU blocks memory bus when executing this instruction
	- No other CPU can access it.
- There is one shared global variable (`lock`) per shared resource.
- Makes the execution wait until the resource is assigned.

### Swap
```C
void Swap(boolean &register, boolean &memory) {
	boolean aux = memory;
	memory = register;
	register = aux;
}

// >>> USAGE <<<
key=true; // entry section
do { swap(lock, key) } while (key == true); // entry section
// CRITICAL SECTION
lock = false; //output section
```

- Swaps the contents of a register with a memory location.

---