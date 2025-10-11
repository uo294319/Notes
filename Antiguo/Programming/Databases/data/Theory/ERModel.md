
---
# Entity/Relationship Model

[Back to index](../../README.md)

---

## Entities vs Attributes

- Entries are defined by a set of attributes.

```mermaid
flowchart TD
	id1---id2
	id1---id3
	id1---id4

	id1["`**Car** *(Entity)*`"]
	id2(["`**ID** *(Attribute)*`"])
	id3(["`**Brand** *(Attribute)*`"])
	id4(["`**Model** *(Attribute)*`"])
```
## Types of Attributes

- Simple or Composite (Formed by several simple ones).
- Single-valued (Simple circle) or Multi-valued (Double circle).
- Derived (Dotted circle) or not.
- Null or not.

## Relations

```mermaid
flowchart LR
	id1-- ". is posted by ." ---id2
	id2-- ". posts ."---id3

	id1["`**Twitterer**`"]
	id2{"`**post**`"}
	id3["`**Tweet**`"]
```
### Characteristics
- Represented with a diamond shape.
- Rol: Description
- Degree:
	- Binary (Two entity association. Common one)
	- Reflexive (Entity associated with itself)
	- N-ary (#N entity association)
- Cardinality
	- One to one (1:1)
	- One to many (1:N or N:1)
	- Many to many (N:N)

	(Specify `min:max` for each side of a relation)
	(Specify `maxL:maxR` for a relation)

### Restrictions
```mermaid
flowchart LR
	E1---R1---E2
	E1---R2---E2

	E1["`**Entity 1** (E1)`"]
	E2["`**Entity 2** (E2)`"]
	R1{R1}
	R2{R2}
```

- **Exclusivity**. Each E1 can participate in R1 or R2 (one at a time).
- **Exclusion**. Each E1 can participate in R1 and R2 but with different E2.
- **Inclusivity**. If E1 have R1 with E2, it must have R2 (with any E2).
- **Inclusion**. If E1 have R1 with E2, it must have R2 with E2 also.

![](../../../../Assets/Programming/Databases/DB_1.png)

### Keys
Used to form relations.
- Primary key - Unique, does not (usually) change.
- Foreign key - Primary key of another entity (establishes a relation).


## Weak Entities
- Its existence depends on another entity
- It is represented with a double rectangle.
- It has an **identifying relation** (double diamond) with another entity.

## Multi-relations (Aggregation)

- We consider relations as if they were entities.
- We can establish a relation between an entity and another relation.
- Now relations always implies ONLY two parties.

![](../../../../Assets/Programming/Databases/DB_2.png)

## Generalization

Joins two or more entities (children) into a general entity (parent).

- **No restrictions**
	![](../../../../Assets/Programming/Databases/DB_3.png)
- **Disjoint** (Children cannot belong to more than one class)
	![](../../../../Assets/Programming/Databases/DB_4.png)
- **Total** (Children must belong to at least one class)
	![](../../../../Assets/Programming/Databases/DB_5.png)
