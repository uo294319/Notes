# Quality, Reviews and SCM
---
[Go Back](../README.md)

---
## Quality
- **Def.** Ability to meet specified requirements and customer or user needs,
- **ISO 25010. Software Product Quality**
	- Suitability
	- Security
	- Portability
	- Performance
	- Compatibility
	- Reliability
	- Operability
	- Maintainability
- **ISO 25010. Quality in use**
	- Effectiveness
	- Efficiency
	- Satisfaction
	- Safety
	- Usability
- Definitions
	- **Quality Assurance (QA)**
		- Planned, systematic pattern of actions.
		- Provide confidence that an item meets the requirements.
	- **Quality Control (QC)**
		- Set of activities designed to evaluate the quality.
	- **Verification and Validation (V&V)**
		- Verification = Are we building the product right?
		- Validation = Are we building the right product?
- Quality costs
	- **Cost of Compliance**
		- Increases with the level of quality
		- Include costs of prevention and evaluation
	- **Cost of Failures**
		- Decreases with the level of quality
		- Include cost of internal and external failures.
	- **Objective**: Find optimal trade-off point between them.
---
## Reviews
- **Definition**
	- Present a work to obtain comment or approval
	- Objective. Early defect detection and reducing unnecessary rework
- **Types (formal to informal)**
	- **Inspections**. Team with different perspectives follow a defined systematic process
	- **Technical reviews**. More formal peer-review.
	- **Peer Review**. Other parties look for non-compliance with specification.
	- **Walk-Through**. Author exposes work and request questions and comments.
- **Roles**
	- **Director**. Responsable or chief. Allocates resources.
	- **Moderator**. Leads the meeting.
	- **Author**. Exposes the reviewed work/material.
	- **Reviewer**. Detects defects in the reviewed work/material.
	- **Secretary**. Records and documents the review.
- **Process**
	1. **Planning**. Calendar, material and attendees
	2. **Start**. Objectives and additional information.
	3. **Preparation**. Reviewers examine the artefact
	4. **Meeting**. Reviewers present the results. Generate a Review report.
	5. **Rebuild and follow-up**. Update and verify changes are included.
---
## Software Configuration Management (SCM)
### Introduction
- **Def**. Set of activities to manage changes throughout the whole life cycle
- **Objectives:**
	- Maintain integrity
	- Monitor and evaluate changes
	- Product visibility for whole team
- **Standard IEEE 828**
- **Concepts**
	- **Hardware Configuration Item (HWCI)**. Hardware component models and configurations.
	- **Computer Software Configuration Item (CSCI)**. Software system or module.
	- **Software Configuration Item (SCI)**. Software related artefact (docs, plans, code, tests...)
	- **Baseline**. SCI in a stable state
	- **Version**. State of a configuration item
	- **Release**. Version ready for distribution.
### Control Process (IEEE 828)
1. Request and registration
2. Evaluation
3. Approval or disapproval
4. Implementation and verification
### Environment Separation
- **Def**. Having operational and test versions for different purposes.
- **Environments:**
	- **Development**
	    - Purpose: Individual component development and early testing.
	    - Activities: Coding, debugging, unit testing.
	- **Integration**
	    - Purpose: Validate interactions between components.
	    - Activities: Integration testing, early system validation.
	    - Notes: Often includes **Continuous Integration (CI)** pipelines.
	- **Pre-production**
	    - Purpose: Final validation before release.
	    - Activities: Acceptance testing, performance testing, user training.
	    - Often mirrors production setup.
	- **Production**
	    - Purpose: Real-world usage by end-users.
	    - Activities: Live operations, monitoring, incident response.
	    - Must be stable and secure.
---