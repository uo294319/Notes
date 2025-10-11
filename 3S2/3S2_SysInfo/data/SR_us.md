# User Stories Elaboration
---
[Go Back](../README.md)

---
## Case study
- Definition
	- Once formailzed a contract with the client, the team is tasked with building the software.
	- Based on the **Definition of the Offer** included in the solicitation documents.
- Objective
	- Define the details of the system to implement
	- Define the tasks to be performed incrementally
	- Result: Product Backlog -> Sprint Backlog
- First we define:
	- General Objective
		- What the client wants.
	- Scope
		- What should and should not be done as part of the project.
		- For that we identify the main processes.
	- Stakeholders 
		- Everyone that take part in the software or could benefit from it.
- Secondly, we identify user requirements
	1. Identify needs and objectives
	2. Identify functional and non-functional requirements
	3. Evaluate alternatives (similar systems / contracting services)
	4. Solution description (decisions, integration and priorities)
- User Stories
	- The customer (Product Owner) provides the team with the requirements.
	- Includes conversations and acceptance criteria.
	- Card format: `As a [role] I want [feature] for [business value]`
---
## Elaboration of the Product Backlog
- Done during the sprint Planning. Meeting 1
- Refinement of US starting by the highest priority
	- Divide epic US into smaller ones
		- Should be doable in a sprint
		- Express a single independent function
	- Include Acceptance criteria
		- Details and conditions to be met.
		- Express users needs through conversations with the PO.
		- Are not acceptance tests.
	- Conversations
		- Raise questions about the details of the acceptance criteria
		- They should be reflected in the acceptance criteria.
---
## Elaboration of the Sprint Backlog
- Done during the sprint Planning. Meeting 2
- Previous US are in the product backlog
- Make commitment (move to sprint backlog)
	- Select a set of them with highest priority that can be done in an sprint.
	- Complete the acceptance criteria describing business rules or scenarios.
- When completing the acceptance criteria some new US may appear.
	- They may be added in the sprint backlog or in the product backlog.
---
## Other
- Prototypes
	- Acceptance criteria do not include all the details about user interaction.
	- Prototypes specify the rest of details.
- Database
	- Done incrementally. Each sprint adds the necessary tables and columns
	- Use data models (domain class model and entity-relationship model)
	- Steps: Entities -> Relationships -> Attributes
---