
---
# Virtual Memory Management Policies

[Back to index](../README.md)

---
## Introduction
- Software required to manage virtual memory (part of the OS).
### Reading policies
- When do we need to load a page to MM?
- **On Demand Paging**
	- Pages are loaded to MM when referenced by the CPU
	- Principle of locality reduces page faults.
	- On Pure Demanding Paging processes start with no page at MM.
- **Previous Paging**
	- More than one page loaded in a single page fault.
	- This was never proven.
### Location Policies
- Where do we need to load a page to MM?
- For paging location is not important.

---
## Resident Set Management
### Definition
- Set of pages of a process loaded to the MM.
- OS determines this set size
- Small size $\implies$ More processes in MM but higher page fault rate per process.
### Assignment Policies
- Maximum number of used frames per process.
	- Low $\text{\#frames}$ $\implies$ Danger of hyper-paging ($\text{\#pages} >> \text{\#frames}$) 
		- More multiprogramming rate but also more page faults.
	- High $\text{\#frames}$
		- Less page faults but also less multiprogramming rate.
- Minimum number of assigned frames per process.
	- Defined by hardware architecture.
- **Types**:
	- Fixed assignation ($\text{\#frames}$ assigned when created)
	- Variable assignation ($\text{\#frames}$ varies on process behaviour)
### Replacement policies
- On some page faults a victim page in the MM is replaced.
- Cases:
	- No free frames in MM.
	- Reached the maximum $\text{\#frames}$ for a process.
- Implementation:
	- FIFO algorithm (victim page is the older in memory)
	- Optimal algorithm (victim page is the one that will be used latter)
	- Last Recently Used (victim page is the one that was less recently used)
	- Working set strategy
		- We have a constant $\Delta$ that is a number of references.
		- The working set is the last $\Delta$ references

---