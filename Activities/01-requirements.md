# Requirements
Narrower scope than Business Analysis which analyzes the entire environment and recommends building the software system as part of the overall business solution.

Identify the stakeholders as the sources of information.

Ensures the stakeholders drive system functionality, not the developers.

## Types of Requirements
### Business requirement
High-level business goal.
### User requirement
Broad description of a goal or task performed by users.
### Functional requirement
Specific behaviour and output under specific conditions and input.
### System requirement
Technical constraint such as operating environment, technologies, interfaces, data.
### Business rule
Business constraint such as laws, regulations, policies, standards.
### Constraint
Restriction imposed on the solution.  External dependency.
### Quality requirement
External: Accessibility (i16n), accuracy, adaptability, availability, configurability, correctness, defect rate, efficiency, integrity, interoperability, performance (responsiveness, throughput), reliability (error detection, fault tolerance, recovery, robustness), safety, scalability, security, supportability, usability

Internal: Modifiability (extensibility, maintainability, portability), flexibility, readability, reusability, simplicity, testability, understandability

Business: Time to market, cost and benefit, system lifetime, targeted market, rollout schedule, integration with other systems

Architecture: Buildability, conceptual integrity, correctness and completeness

## User Stories
User Stories are a placeholder for a conversation.

User Stories differ from full requirements in that User Stories provide only enough detail to make a reasonable estimate for time to implement.

Format: As a *(type of user)*, I want *(some goal)* so that *(some reason)*.

Characteristics: Independent, Negotiable, Valuable, Estimateable, Small, Testable

*Epic*: User Story consisting of multiple User Stories

*Persona*: Name, picture, role, backstory, motivation soundbyte

Split User Stories by: Workflow, Quality attributes, Positive/Negative cases, External dependencies, More specific user types, Spikes

Each User Story is expanded into scenarios and acceptance criteria at the beginning of the iteration.

## Elicitation, Gathering, Generation
Understand the domain, gather user stories:

- One-on-one interviews with stakeholders
- Observe current activities of potential users
- Focus groups
- Surveys, questionnaires
- Research

Prioritize stories:

- MoSCoW: M (must), S (should), C (could), W (won’t)
- High, Medium, Low

Output: Product backlog

## Analysis
Each user story is expanded into scenarios such that they are:

- “Given … When … Then …”
- Complete
  - All range of inputs and outputs
  - All constraints
  - All events
  - All boundary cases
  - All potential states
  - All security roles/rights/scopes
- Consistent (no conflicting requirements)
- Implementation-free
- Unambiguous
- Traceable (uniquely identified)
- Quantitative
- Achievable (technically feasible)
- Verifiable (testable)
- No overlap
- Modelled/diagrammed

## Documentation
- Product Vision Statement: For *(target customers)* who *(need/opportunity)*, our *(solution name)* is a *(product category)* that *(capabilities)*, unlike *(alternatives)* our solution *(differentiation)*
- Requirements (grouped by similarity)
  - Unique ID (e.g., Topic.Section.Title)
  - Summary
  - Rationale
  - Owner
  - Constraints
  - Dependencies
  - Success metrics/Acceptance criteria/Conditions of satisfaction
  - Priority
  - Change history
- Assumptions
- Risks

## Validation
Formal reviews are performed by analysts and stakeholders.

Prototypes are used for validation by development team.

Acceptance tests are written.

## Executable Specification
Acceptance tests are automated.

## Minimum Viable Product
The minimum set of user stories that, when implemented and released, are usable and beneficial to the customer.

# References
Bogue, Robert. *Gathering Good Requirements for Developers*, [PluralSight](http://www.pluralsight.com/courses/gathering-good-requirements-developers), 2014.

Halabi, Mohamad. *Software Engineering Essentials*, [PluralSight](http://www.pluralsight.com/courses/software-engineering-essentials), 2015.

Jarrell, Jeremy. *Creating Effective User Stories*, [PluralSight](http://www.pluralsight.com/courses/creating-effective-user-stories), 2014.

