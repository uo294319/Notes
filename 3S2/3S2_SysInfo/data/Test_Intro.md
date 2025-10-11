# Introduction to Software Quality
---
[Go Back](../README.md)

---
## Definitions
- Process of executing a program with the intent of finding failures
- **Objectives**
	- Provide stakeholders with information about the quality
	- Good test case = High probability of finding a failure.
	- Successful test case = Failure found
- **Standard ISO 29119**
- **Testing vs Debugging**
	- Testing is used to find failures
	- Debugging is used to find why that failures happen.
---
## Types
- **Testing types**
	- **Static**. Examines code without executing.
	- **Dynamic**. Executes a test item.
- **What happened?**
	- **Error** = Human mistake
	- **Failure** = Unexpected behaviour
	- **Defect, Fault or Bug** = Component or system flaw
---
## Dynamic Testing Process
1. **Test Basis**. Specification of the component or system under test
2. **Testing Techniques**. Methodology can vary depending on the test basis.
3. **Test design and implementation**
	1. **Identify Test Situations**
	2. **Design Test Cases**. Expected output with certain inputs and initial conditions.
	3. **Implement Test Cases**. For example `JUnit`.
4. **Execution and reporting**
	1. **Execute** the Test Cases
	2. **Compare** obtained output with expected one
	3. **Report** findings.
5. **Debug**. Find and correct those failures.
---