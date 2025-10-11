
---
# State

[Back to index](../README.md)

---

## Description

Allows to modify the behaviour of an object depending on a internal state.

## Characteristics

- 

## UML

```mermaid
classDiagram
direction LR

Context --o State
State <|-- State1
State <|-- State2

class Context {
	<< C >>
	- State state
	+ goNext() void
	+ setState(State) void
}

namespace States {
	class State {
		<< I >>
		+ goNext(Context) void
	}

	class State1 {
		<< C >>
		+ goNext(Context) void
	}
	
	class State2 {
		<< C >>
		+ goNext(Context) void
	}
}
```
## Code

```java
public class Context { 
	private State state;

	public Context() {
		// Initial State
		state = new State1
	}

	public void goNext() {
		state.goNext(this);
	}

	public void setState(State s) {
		state = s
	}
}

public class State1 implements State {
	@Override
	public void goNext(Context c) {
		c.setState(new State2)
	}
}

public class State2 implements State {
	@Override
	public void goNext(Context c) {
		c.setState(new State1)
	}
}
```