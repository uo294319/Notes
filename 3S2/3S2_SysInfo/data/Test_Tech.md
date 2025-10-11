# Testing Techniques
---
[Go Back](../README.md)

---
## Introduction
- **Test Technique **
	- Procedure or criterion that allows to find a set of good test cases
	- Maximize the probability of finding failures while meeting time and cost limits.
- **Test Case**
	- Set of inputs, execution conditions and expected results for a particular objective.
	- The set of test cases is called Test Suite
- **Types of testing**
	- **White Box**
		- Based on the source code.
		- Example. Condition or decision Coverage
	- **Black Box**
		- Cannot rely on the code (incorrect, incomplete or unavailable)
		- Example. Equivalence Partitioning
---
## Equivalence Partitioning
1. **Specification** for Component/System under test
2. Identify **Equivalence Classes**
	1. Examine **input or output conditions**
	2. Divide input conditions into disjoint equivalence classes
		1. Enumerations. Add 1 class for other
		2. Ranges. Classes for the limit values, below and above.
		3. Logical values
	3. Divide different behaviour classes into smaller ones (Hierarchy)
3. Create **Test Cases** to cover the Equivalence Classes.
	1. Valid classes are covered with the fewer number of test cases possible.
	2. Each invalid class requires a independent test case
---
## Testing Process (ISO 29119)
1. Organization Testing Process. Obtain Policy and testing strategy.
2. Testing Management Processes. Obtain Plan, control and guidelines
	1. Planning
	2. Control and Result Tracking
	3. Ending
3. Dynamic Testing Processes
	1. Test Design & Implementation
	2. Test Environment
	3. Test Execution
	4. Report of issues on tests (if found)
---
## V-shaped Model

| Development          | Testing             |
| -------------------- | ------------------- |
| User Requirements    | Acceptance Testing  |
| System Requirements  | System Testing      |
| Architectural Design | Integration Testing |
| Detailed Design      | Component Testing   |
| Implementation       | Unit Testing        |

---