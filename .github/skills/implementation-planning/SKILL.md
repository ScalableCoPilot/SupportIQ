---
name: implementation-planning
description: Creates or updates a dependency-aware, feature-wise implementation plan from an approved PRD. Breaks scope into epics, features, tasks and subtasks with acceptance criteria, dependencies, estimates, risks and traceability. Use after PRD approval and before implementation.
---

# Implementation Planning

## Mission

Convert approved business requirements into a realistic, reviewable and executable engineering plan. Produce enough detail for developers and coding agents to implement work in small, independently verifiable increments.

This skill is technology-neutral. Discover the repository's actual architecture, languages, frameworks, conventions and deployment model before proposing technical work.

## Preconditions

1. Locate the approved PRD. Prefer an explicit path supplied by the user; otherwise inspect the repository's documented requirements structure.
2. Confirm that the PRD is marked approved/baselined. If approval is unclear, stop and ask for confirmation; do not treat a draft as approved.
3. Read relevant baseline, requirement inventory, traceability, assumptions, decisions, risks and open questions.
4. Read `.github/copilot-instructions.md` and relevant existing skills, especially software architecture, backend architecture and senior developer skills.
5. Inspect the repository sufficiently to understand current implementation, conventions and existing reusable components.
6. Do not edit application source code during planning.

If a critical requirement is ambiguous, record it as an open question or assumption. Do not invent business rules.

## Planning principles

- Preserve approved scope and requirement IDs. Every feature must trace to one or more PRD requirement IDs.
- Separate business outcomes from technical implementation choices.
- Prefer vertical features that deliver an observable user or system capability.
- Design tasks to be independently implementable, testable and reviewable.
- Identify dependencies explicitly; avoid circular dependencies.
- Prefer incremental delivery and a thin end-to-end slice before broad layers of infrastructure.
- Reuse existing architecture and code where appropriate. Do not propose rewrites without evidence and approval.
- Include non-functional requirements: security, privacy, accessibility, performance, reliability, observability, maintainability, deployment and operations where applicable.
- Include migrations, configuration, feature flags, backward compatibility and rollback tasks when relevant.
- Do not make estimates appear precise. State the estimation unit and assumptions.
- Flag cross-cutting work once and link dependent features to it; avoid duplicating the same task in multiple places.

## Required hierarchy

Use this hierarchy:

- **Epic**: a major business or technical outcome.
- **Feature**: a coherent capability that can be demonstrated and accepted.
- **Task**: a meaningful engineering deliverable, ideally small enough for one focused work session or pull request.
- **Subtask**: a concrete implementation or verification step.

Each item receives a stable ID:
- Epic: `EPIC-001`
- Feature: `FEAT-001`
- Task: `TASK-001`
- Subtask: `SUB-001`

Never reuse an ID. When reorganizing, preserve IDs where the underlying work remains the same. Record superseded IDs and replacements.

## Required planning workflow

### 1. Establish the baseline

Record:
- PRD path, version/date and approval status
- repository branch/commit if available
- existing application structure and stack discovered
- existing capabilities that can be reused
- scope exclusions and constraints
- assumptions and unresolved questions

### 2. Build requirement traceability

For each PRD requirement:
- preserve its original ID and wording/reference
- classify it as functional, non-functional, constraint or operational
- map it to one or more features
- identify acceptance criteria
- flag requirements with no planned coverage

Every in-scope requirement must map to at least one feature or have a documented reason for exclusion.

### 3. Define epics and features

For each epic, describe the outcome and boundaries.

For each feature include:
- ID and name
- user/business value
- description and in-scope behaviour
- out-of-scope behaviour
- linked PRD requirement IDs
- user roles/actors and key flows, if applicable
- acceptance criteria written as observable outcomes
- dependencies and integration points
- data/API/UI impact as applicable
- security and privacy considerations
- observability and operational considerations
- risks, assumptions and open questions
- definition of done

Avoid features that are merely technical layers (for example, “create all database tables”) unless the work is genuinely a shared enabling capability.

### 4. Decompose into tasks and subtasks

For each feature:
- identify design, backend, frontend, data, integration, configuration, testing, documentation and deployment tasks as applicable
- identify unit, integration, contract, end-to-end, accessibility, performance and security tests as relevant
- include error handling, validation, authorization and audit/telemetry work
- identify data migration and rollback work when needed
- define task dependencies and parallelizable tasks
- make each task have a clear output and verification method

A task should normally:
- have one owner role (not a named person unless supplied)
- have a clear action and deliverable
- be small enough to review
- have testable completion criteria
- not hide multiple unrelated outcomes

Do not create subtasks just to make the list longer. Use them when they improve execution clarity.

### 5. Sequence the work

Create a dependency-aware order:
- foundations and high-risk unknowns first
- architecture decisions and shared contracts before dependent implementation
- thin end-to-end vertical slice early
- features in business-priority order
- testing and hardening before release
- deployment, migration and operational readiness before production release

Call out critical path, parallel work, external dependencies and milestones. Do not infer calendar dates or team capacity unless supplied.

### 6. Estimate and assess risk

Use a declared estimation scale (for example, story points or T-shirt sizes). Estimate at task or feature level consistently. State that estimates are relative, not commitments.

For each significant risk record likelihood, impact, mitigation, owner role and trigger/contingency. Distinguish confirmed facts from assumptions.

### 7. Validate plan completeness

Check:
- all approved requirements are mapped
- each feature has acceptance criteria
- every task has a deliverable and verification approach
- dependencies are valid and acyclic
- non-functional and operational work is covered
- no duplicate or orphan tasks exist
- risks and open questions are visible
- scope exclusions are explicit
- the plan can be executed without silently changing the PRD

### 8. Present for approval

Create/update the plan artifacts, then summarize:
- proposed epics/features and sequencing
- scope and traceability coverage
- critical dependencies and risks
- assumptions/open questions requiring decisions
- estimates and caveats
- recommended first feature/slice

Mark the plan `Draft – Pending Approval`. Do not mark it approved or start implementation until the user or authorized project owner approves it.

## Required artifacts

Create or update:

1. `docs/implementation/implementation-plan.md`
   - baseline and scope
   - architecture/technical approach summary
   - epics and feature catalogue
   - dependency graph/order
   - milestones and release slices
   - estimation assumptions
   - risks, assumptions and open questions
   - approval history

2. `docs/implementation/feature-task-board.md`
   - all feature/task/subtask IDs
   - titles, requirement links, dependencies, priority, estimate and status
   - acceptance/verification references
   - owner role if known

3. `docs/implementation/decisions/`
   - create an Architecture Decision Record only when a meaningful technical decision is needed
   - do not duplicate decisions already recorded in the project decision log

4. Update the requirement traceability artifact only when the mapping is approved or the repository convention explicitly allows proposed mappings. Clearly label proposed changes.

## Default status vocabulary

Plan: `Draft`, `Pending Approval`, `Approved`, `Superseded`.

Work item: `Not Started`, `Ready`, `In Progress`, `Blocked`, `In Review`, `Done`, `Deferred`, `Cancelled`.

Do not use `Done` during planning.

## Output format

After planning, report:
1. files created/updated
2. epics and feature count
3. requirement coverage and uncovered requirements
4. critical path and dependencies
5. key risks and open questions
6. assumptions made
7. approval required and the recommended next action

## Stop conditions

Stop and ask rather than guessing when:
- no approved PRD can be identified
- the PRD conflicts with the baseline in a way that changes scope
- a business rule materially affects architecture or estimates and is unresolved
- requested scope exceeds the approved PRD
- a proposed technical choice would create a major irreversible commitment without adequate information
