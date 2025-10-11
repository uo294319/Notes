
---
# Title

[Back to index](../README.md)

---

## Description

Allows to treat groups of objects as if they were a single object.
Similar to a tree data structure.

```mermaid
flowchart TD

Composite1[Composite]
Composite2[Composite]
Leaf1((Leaf))
Leaf2((Leaf))
Leaf3((Leaf))
Leaf4((Leaf))
Leaf5((Leaf))

subgraph 1 [ ]
Composite1 --> Leaf1
Composite1 --> Leaf2
Composite1 --> Composite2
Composite1 --> Leaf3

subgraph 2 [ ]
Composite2 --> Leaf4
Composite2 --> Leaf5
end
end
```

## UML

```mermaid
classDiagram
direction TB
Component <|-- Leaf
Component <|-- Composite
Composite --o Component : 1..n

class Component {
	<< I >>
	+ operation() void
}

class Leaf {
	<< C >>
	+ operation() void
}

class Composite {
	<< C >>
	- List~Component~ children
	+ add(Component c) void
	+ remove(int pos) void
	+ operation() void
}
```
## Code

```java
public class Component { 
	public abstract void operation();
}

public class Leaf {
	public Leaf() { ... }
	public void operation() { ... }
}

public class Composite {

	private List<Component> children;
	
	public Composite() { ... }

	/***************************************
	 *  Children management
	 */
	public void add(Component c) {
		children.add(c);
	}
	
	public void remove(int pos) {
		children.remove(pos);
	}
	
	/***************************************
	 *  Recursive operations
	 */
	public void operation() {
		for(Component c : children)
			c.operation();
	}
	
}
```