---
name: requirements-analysis
description: Conduct end-to-end product and business requirements analysis for any software project. Use when analyzing existing requirements documents, discovering requirements, interviewing stakeholders, identifying gaps and conflicts, documenting evidence and decisions, validating requirements, or preparing an approved PRD and supporting requirements artifacts.
---

# Requirements Analysis Skill

## 1. Purpose

This skill manages the complete requirements lifecycle, from understanding the initial business need to producing approved, implementation-ready requirements.

It is designed to work across different projects, industries, technologies, and delivery approaches.

The skill must:
- Analyze existing requirements documents and other project sources.
- Understand the business problem, objectives, and expected outcomes.
- Identify missing, incomplete, ambiguous, conflicting, and assumed requirements.
- Conduct structured stakeholder interviews.
- Document business, functional, non-functional, and technical requirements.
- Maintain evidence, assumptions, decisions, risks, and open questions.
- Validate requirements with stakeholders.
- Generate a comprehensive PRD after requirements approval.
- Maintain traceability between requirements, user stories, and acceptance criteria.

**Important:** Requirements analysis and implementation planning are separate activities. Do not begin implementation planning until the approved requirements and the stakeholder's authorization are available.

## 2. Project Independence

Do not assume any particular:
- Programming language or framework.
- Frontend or backend architecture.
- Database or storage technology.
- Cloud provider or hosting environment.
- Authentication or authorization approach.
- Third-party service or integration.
- AI platform or model.
- Development methodology.

Use the information provided by the project owner and its source documents.

If a technical choice has not been confirmed, classify it as an assumption, proposal, or open question.

For every new project:
1. Identify the project name and purpose.
2. Locate the original requirements and supporting documents.
3. Read the available project instructions.
4. Identify the expected stakeholders and intended users.
5. Identify project-specific constraints and approval processes.
6. Adapt the analysis to the actual project.

Never copy requirements, assumptions, technology decisions, or business rules from another project.

## 3. Core Principles

Follow these principles throughout the workflow:

1. Treat original source documents as evidence, not automatically as approved requirements.
2. Do not invent business requirements.
3. Do not silently resolve conflicting information.
4. Preserve the original source documents.
5. Ask one clarification question at a time.
6. Prioritize questions based on business impact, risk, and uncertainty.
7. Keep confirmed facts separate from assumptions and recommendations.
8. Record the source of every important requirement.
9. Maintain stable IDs for requirements and decisions.
10. Do not treat silence as stakeholder approval.
11. Obtain explicit approval at the defined approval gates.
12. Update affected documentation when a requirement changes.

## 4. Requirement Classification

Classify findings using the following categories:

| Classification | Meaning |
|---|---|
| Confirmed | Explicitly supported by a reliable source or stakeholder response |
| Missing | Expected information is not available |
| Incomplete | Information exists but is insufficient |
| Ambiguous | More than one interpretation is possible |
| Conflicting | Sources or statements contradict one another |
| Assumption | A temporary statement that has not been verified |
| Recommendation | A proposed improvement or solution |
| Out of Scope | Explicitly excluded from the project |
| Deferred | Recognized but postponed for a later phase |

Do not convert assumptions or recommendations into confirmed requirements without validation.

## 5. Requirement Status

Use these statuses:

- Draft
- Under Review
- Confirmed
- Approved
- Rejected
- Deferred

A confirmed requirement is not automatically an approved requirement.

Only mark a requirement as Approved after the appropriate stakeholder explicitly approves it.

## 6. End-to-End Workflow

Follow these phases in sequence.

### Phase 1: Project Understanding and Source Analysis

**Objective:** Understand the project and analyze all available source material.

Activities:
1. Read the project-level instructions.
2. Locate and inspect the original requirements document.
3. Review relevant supporting documents, diagrams, spreadsheets, and existing system information.
4. Understand the business problem and project objectives.
5. Identify stakeholders, users, systems, and external dependencies.
6. Extract requirements without changing their original meaning.
7. Identify missing, incomplete, ambiguous, conflicting, and assumed information.
8. Record references to the source document, section, page, or other available evidence.

Produce:
- Project Overview
- Source Document Inventory
- Baseline Requirements Summary
- Initial Requirements Inventory
- Requirements Gap Analysis
- Ambiguity and Conflict Register
- Initial Assumptions Register
- Initial Open Questions

**Approval Gate 1 — Initial Analysis Review**

Present the initial findings to the project owner.

Ask for confirmation or corrections before proceeding to detailed discovery.

### Phase 2: Stakeholder Discovery and Interviews

**Objective:** Resolve uncertainties and discover missing requirements.

Interview stakeholders one question at a time.

Question priorities:
1. Business objectives and expected outcomes.
2. Target users and stakeholder responsibilities.
3. Current business process and existing problems.
4. Expected future workflows.
5. Functional capabilities.
6. Business rules and exceptions.
7. Data requirements.
8. Integrations and external dependencies.
9. Security, privacy, and access control.
10. Performance, scalability, availability, and other quality expectations.
11. Reporting, monitoring, and operational needs.
12. Constraints, priorities, and release expectations.

Interview rules:
- Ask only one question in each interaction.
- Explain briefly why an important clarification is needed.
- Avoid asking questions already answered by reliable evidence.
- Use follow-up questions when an answer is incomplete.
- Do not assume an unanswered question has been approved.
- Record the stakeholder's response accurately.
- Identify whether the response confirms an existing requirement or introduces a new one.

Produce:
- Stakeholder Register
- Interview Questions and Answers
- Discovery Findings
- Updated Requirements Inventory
- Updated Assumptions Register
- Updated Open Questions Register
- Decision Log

**Approval Gate 2 — Discovery Review**

Present the discovery findings and unresolved questions.

Proceed only after the project owner agrees that the discovery findings are sufficiently complete.

### Phase 3: Business and System Analysis

**Objective:** Convert discovered business needs into structured, testable requirements.

Analyze the relevant areas based on the project scope.

#### 3.1 Business Requirements
- Business problem.
- Business objectives.
- Expected business outcomes.
- Success measures and KPIs.
- Business constraints.
- Business priorities.

#### 3.2 Stakeholders and User Roles
- Stakeholder groups.
- User personas.
- User responsibilities.
- Permissions and access requirements.
- Administrative roles.

#### 3.3 Functional Requirements
- System capabilities.
- Features and modules.
- User actions.
- System responses.
- Validation rules.
- Error handling.
- Business workflows.
- Alternative and exception flows.

#### 3.4 Non-Functional Requirements
Evaluate applicable quality attributes:
- Performance and response times.
- Scalability.
- Availability and reliability.
- Security.
- Privacy and compliance.
- Maintainability.
- Accessibility.
- Usability.
- Compatibility.
- Observability and monitoring.
- Backup and recovery.

Do not invent numerical targets. Record missing targets as open questions.

#### 3.5 Business Rules
Document:
- Business policies.
- Validation rules.
- Calculations.
- Eligibility conditions.
- Approval rules.
- Workflow conditions.
- Exceptions.

#### 3.6 Data Requirements
Analyze:
- Data entities and relationships.
- Required fields and validations.
- Data ownership.
- Data lifecycle and retention.
- Data migration.
- Data privacy and protection.
- Import and export requirements.

#### 3.7 Integration Requirements
Identify applicable:
- Internal systems.
- External services.
- APIs.
- Events and messaging.
- Authentication between systems.
- Data exchange.
- Failure handling and retries.

#### 3.8 Technology and Architecture Constraints

Capture only technology and architecture constraints that are supported by project evidence or explicitly confirmed by stakeholders.

Separate mandatory constraints from recommendations.

#### 3.9 Specialized Requirements

Depending on the project, analyze applicable areas such as:
- AI and machine learning.
- Reporting and analytics.
- Automation.
- Notifications.
- Payments.
- Multi-tenancy.
- Regulatory compliance.
- Localization.
- Mobile or offline functionality.

Do not create irrelevant sections simply to complete a template.

#### 3.10 Risks and Dependencies
Identify:
- Business risks.
- Technical risks.
- Operational risks.
- External dependencies.
- Third-party dependencies.
- Delivery constraints.

Produce:
- Business Requirements
- Functional Requirements
- Non-Functional Requirements
- Business Rules
- User Roles and Permissions
- Workflow and Use Case Documentation
- Data Requirements
- Integration Requirements
- Applicable Specialized Requirements
- Risks and Dependencies Register

### Phase 4: Evidence, Assumptions and Decision Management

**Objective:** Maintain an auditable record of why requirements exist and how decisions were made.

Maintain the following registers.

#### Evidence Register
Record:
- Evidence ID.
- Description.
- Source.
- Source location or reference.
- Related requirement IDs.
- Evidence date, when available.
- Notes.

#### Assumptions Register
Record:
- Assumption ID.
- Assumption description.
- Reason.
- Impact if incorrect.
- Validation owner.
- Status.

#### Decision Log
Record:
- Decision ID.
- Decision description.
- Context and alternatives.
- Decision owner.
- Date, when available.
- Impacted requirements.
- Status.

#### Open Questions Register
Record:
- Question ID.
- Question.
- Why clarification is needed.
- Business or technical impact.
- Priority.
- Owner.
- Status.

#### Change Log
Record:
- Change ID.
- Description of the change.
- Previous requirement.
- Updated requirement.
- Reason.
- Impacted artifacts.
- Approval status.

Never fabricate evidence, stakeholder responses, approval dates, or decision owners.

### Phase 5: Requirements Validation and Prioritization

**Objective:** Ensure the requirements are complete, consistent, understandable, and testable.

Review each requirement for:

- Clear and unambiguous wording.
- Unique identification.
- Business justification.
- Source or evidence reference.
- Appropriate classification and status.
- Testability and measurable acceptance conditions.
- Dependencies.
- Scope alignment.
- Consistency with other requirements.
- Security and privacy implications, where applicable.

Identify duplicate requirements and resolve them through documented review rather than silently deleting them.

#### Prioritization

Use MoSCoW when appropriate:

- Must Have
- Should Have
- Could Have
- Won't Have (this release)

Treat priorities as proposals until the authorized stakeholder approves them.

#### Traceability

Maintain relationships between:

Business Requirements → Functional/Non-Functional Requirements → User Stories → Acceptance Criteria → Test Cases

Produce:
- Requirements Validation Report
- Requirements Traceability Matrix
- Prioritized Requirements
- Updated Risk Register
- Final Open Questions
- Requirements Approval Summary

**Approval Gate 3 — Requirements Approval**

Present the complete requirements package.

Ask the authorized stakeholder to explicitly approve:
- Business requirements.
- Functional requirements.
- Non-functional requirements.
- Business rules.
- Scope and exclusions.
- Priorities.
- Outstanding assumptions and accepted risks.

Do not generate the final approved PRD until this approval is received.

### Phase 6: Final PRD Generation

**Objective:** Generate the authoritative Product Requirements Document from approved requirements.

Required inputs:
- Approved requirements.
- Validated business analysis.
- Confirmed stakeholder information.
- Approved scope.
- Accepted assumptions and risks.
- Relevant evidence and decisions.

Use this structure, adapting it to the project:

1. Document Information
2. Executive Summary
3. Problem Statement
4. Business Objectives and Success Metrics
5. Project Scope
   - In Scope
   - Out of Scope
   - Future Scope
6. Stakeholders and User Personas
7. Current and Proposed Workflows
8. Business Requirements
9. Functional Requirements
10. Non-Functional Requirements
11. Business Rules
12. User Roles and Permissions
13. Data Requirements
14. Integration Requirements
15. Specialized Requirements, where applicable
16. User Stories
17. Acceptance Criteria
18. Error and Exception Scenarios
19. Risks, Dependencies and Constraints
20. Assumptions and Open Questions
21. Requirements Traceability
22. Approval and Sign-off

Use clear, consistent, testable language.

Do not add unapproved features or technical decisions to the PRD.

Do not hide unresolved questions. Clearly identify them and their impact.

#### Requirement ID Standards

Use stable IDs:

| Prefix | Meaning |
|---|---|
| BR | Business Requirement |
| FR | Functional Requirement |
| NFR | Non-Functional Requirement |
| RULE | Business Rule |
| ROLE | User Role |
| UC | Use Case |
| WF | Workflow |
| DATA | Data Requirement |
| API | Integration or API Requirement |
| AI | AI Requirement |
| US | User Story |
| AC | Acceptance Criteria |
| TC | Test Case |
| RISK | Risk |
| ASM | Assumption |
| EV | Evidence |
| Q | Open Question |
| DEC | Decision |
| CHG | Change |

Example:
- BR-001
- FR-001
- NFR-001
- US-001
- AC-001

Do not renumber existing IDs unnecessarily. Preserve traceability when requirements change.

**Approval Gate 4 — PRD Review and Approval**

Present the completed PRD and supporting artifacts for review.

Capture requested changes, update the documents, and obtain explicit approval.

Only mark the PRD as approved after stakeholder sign-off.

### Phase 7: Handover to Implementation Planning

**Objective:** Prepare an approved requirements package for the next project lifecycle stage.

This phase does not automatically authorize implementation planning.

Prepare:
- Approved PRD.
- Approved requirements inventory.
- Requirements traceability matrix.
- Approved workflows and use cases.
- Acceptance criteria.
- Evidence and decision registers.
- Accepted assumptions and risks.
- Outstanding dependencies and constraints.

**Approval Gate 5 — Implementation Planning Authorization**

Ask whether the project owner wants to begin implementation planning.

Do not create architecture plans, technical design documents, development tasks, sprint plans, or implementation roadmaps unless explicitly authorized.

## 7. Documentation Management

Use the project's existing documentation structure when available.

If no structure exists, propose a structure appropriate to the project.

A recommended structure is:

```text
docs/
└── requirements/
    ├── baseline/
    ├── analysis/
    │   ├── project-overview.md
    │   ├── baseline-analysis.md
    │   ├── requirements-inventory.md
    │   ├── gap-analysis.md
    │   ├── stakeholder-analysis.md
    │   ├── business-requirements.md
    │   ├── functional-requirements.md
    │   ├── non-functional-requirements.md
    │   ├── business-rules.md
    │   ├── workflows-and-use-cases.md
    │   ├── data-requirements.md
    │   ├── integration-requirements.md
    │   └── risks-and-dependencies.md
    ├── evidence/
    │   ├── evidence-register.md
    │   ├── assumptions-register.md
    │   ├── decision-log.md
    │   ├── open-questions.md
    │   ├── interview-records.md
    │   └── change-log.md
    └── approved/
        ├── PRD.md
        ├── requirements-traceability.md
        └── requirements-approval.md
```

Documentation rules:
- Adapt the structure to the project.
- Reuse existing documents when appropriate.
- Do not create unnecessary or duplicate files.
- Do not create empty placeholder documents.
- Use Markdown unless the project requires another format.
- Keep the original baseline unchanged.
- Update related documents when decisions or requirements change.
- Record approval status and relevant references.
- Maintain a clear distinction between working analysis and approved artifacts.

## 8. Interview and Interaction Rules

During interactive discovery:

1. Present the relevant finding or context.
2. Ask one important question.
3. Wait for the stakeholder's response.
4. Interpret and record the answer.
5. Update affected requirements and registers.
6. Identify whether further clarification is necessary.
7. Ask the next most important question.

Do not present a long questionnaire unless explicitly requested.

Do not repeatedly ask for information already provided.

If the stakeholder does not know an answer, record it as an open question or assumption.

If the stakeholder changes an earlier decision, update the decision log and assess its impact.

## 9. Quality Review Checklist

Before submitting requirements for approval, verify:

- [ ] Original sources have been reviewed.
- [ ] Business objectives are clear.
- [ ] Stakeholders and user roles are identified.
- [ ] Project scope and exclusions are documented.
- [ ] Requirements are uniquely identified.
- [ ] Functional requirements are testable.
- [ ] Applicable non-functional requirements are addressed.
- [ ] Business rules are documented.
- [ ] Important workflows and exceptions are covered.
- [ ] Data and integration needs are understood.
- [ ] Security and privacy needs are considered.
- [ ] Assumptions and open questions are visible.
- [ ] Risks and dependencies are documented.
- [ ] Evidence and decisions are traceable.
- [ ] Requirements are prioritized or explicitly awaiting prioritization.
- [ ] Traceability is maintained.
- [ ] Conflicts and ambiguities are resolved or explicitly recorded.
- [ ] Stakeholder approval is recorded.

## 10. Restrictions

Never:
- Modify or overwrite original source documents.
- Invent stakeholder answers or evidence.
- Convert proposals into approved requirements.
- Silently resolve conflicts.
- Assume an approval that was not explicitly provided.
- Generate the final PRD before requirements approval.
- Start implementation planning without authorization.
- Assume a specific technology stack.
- Create unnecessary documentation or duplicate requirements.
- Remove or rewrite requirements without recording the reason and impact.

## 11. Completion Criteria

Requirements analysis is complete when:

1. The available baseline and supporting sources have been analyzed.
2. Stakeholder discovery has been completed to the agreed level.
3. Business and system requirements have been documented.
4. Gaps, assumptions, risks, decisions, and open questions are recorded.
5. Requirements have been validated and prioritized.
6. The authorized stakeholder has approved the requirements.
7. The final PRD has been generated and reviewed.
8. PRD approval has been explicitly recorded.

The implementation planning phase remains separate and requires its own authorization.