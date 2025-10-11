
---
# Memory Hierarchy

[Back to index](../README.md)

---
## Introduction to Memory Hierarchy
### Hierarchy
1. CPU registers
2. Cache memory
3. Main Memory (MM)
4. Disk Cache
5. Magnetic disk
6. Magnetic tape – Optic disk
## Characteristics
From top (1) to bottom (6):
- Cost decreases (per bit).
- Capacity increases.
- Access time increases.
- CPU access frequency decreases.
---
## Principle of Locality
- Memory accesses tend to be to adjacent positions.
	- Sequential programs, iterative structures, vectors...
- When an address is accessed it is probable that it will be accessed again.
- +performance = less access to lower level memories.
	- Highly accessed data stores in cache memory.

---
## Hierarchy's operation
### Main Memory
- Most important memory.
- Is directly and explicitly accessed by the CPU.
- CPU only deals with MM addresses.
### Cache Memory
- In in between the CPU registers and the MM.
- Has small size and high access speed.
- Every piece of data goes through it.
- Is invisible to the CPU
### Disk (Secondary storage)
- Can contain parts of processes.
- Data goes to MM only when needed.
### Disk Cache
- Is an intermediate buffer between the disk and MM
- Usually implemented in the MM by software.

---