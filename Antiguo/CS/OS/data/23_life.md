
---
# Processes life cycle

[Back to index](../README.md)

---

## Simple model

```mermaid
stateDiagram
    direction LR
	A1: Not Running
	A2: Running


    [*] -->  main: Enter
    state main {
		A1  -->  A2: Dispatch
		A2  -->  A1: Pause
	}
	main  --> [*]: Exit
    
```
- Processes start at `not running` state.
- Do not work for multiprogramming.

---
## 5-state model

```mermaid
stateDiagram
    direction LR
	A1: New
	A2: Ready
	A3: Running
	A4: Blocked
	A5: Exit


    A1 -->  main: Admit
	state main {
		direction TB
		A2 --> A3: Dispatch
		A3 --> A2: Timeout
		A3 --> A4: Event wait
		A4 --> A2: Event occurs
	}
	main --> A5: Release
    
```
- There can be not-admitted processes (while being loaded to memory).
- Admitted processes go to `ready` state.
- Processes can end because:
	- Special ending instruction.
	- `exit` system call.
	- Exception.
	- Direct intervention of the OS.
	- Parent process kills it.
	- Other reasons.
- Queues for the `ready` and `blocked` state are needed.

---
## 7-state model

```mermaid
stateDiagram
    direction TB
	A1: New
	A2: Ready
	A3: Running
	A4: Blocked
	A5: Exit
	A6: Ready Suspended
	A7: Blocked Suspended

	A1 -->  main: Admit
	
	state main {
		direction LR
		state activated {
			direction TB
			A2 --> A3: Dispatch
			A3 --> A2: Timeout
			A3 --> A4: Event wait
			A4 --> A2: Event occurs
		}
	
		state suspended {
			direction TB
			A7 --> A6: Event occurs
		}
		
		activated --> suspended: suspend
		suspended --> activated: activate
	}
	main --> A5: Release

```

- Allows the OS to suspend processes if it runs out of memory.
- Admitted processes can go to `ready` or `ready suspended` states.