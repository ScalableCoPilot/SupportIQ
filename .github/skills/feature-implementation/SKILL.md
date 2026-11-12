---
name: feature-implementation
description: Implements one approved feature or task from the implementation plan using existing repository conventions, architecture and tests. Use after the implementation plan is approved and the target work item is selected.
---

# Feature Implementation

## Mission

Deliver the selected feature/task as a small, production-quality, verifiable change while preserving approved requirements and the existing architecture.

This skill orchestrates implementation. Reuse the repository's existing `engineering-software-architect`, `engineering-backend-architect` and `engineering-senior-developer` skills where relevant. Do not copy or override their specialist guidance.

## Preconditions

Before editing:
1. Read `.github/copilot-instructions.md`.
2. Read this skill and all relevant specialist skills.
3. Read the approved PRD and approved implementation plan.
4. Read the selected feature specification and task board entries.
5. Confirm the selected item is `Ready` or explicitly authorized for work.
6. Inspect current branch, working tree, related source files, tests and conventions.
7. Check dependencies and confirm prerequisite tasks are `Done`.
8. Identify existing uncommitted changes. Never overwrite or discard user work.

If the plan is not approved, the item is blocked, acceptance criteria are missing, or dependencies are incomplete, stop and explain what is needed.

## Execution rules

- Work only on the selected feature/task and its necessary supporting changes.
- Do not implement unrelated cleanup, refactoring or speculative enhancements.
- Do not change approved requirements or acceptance criteria silently.
- Prefer the smallest coherent vertical slice.
- Follow existing naming, layering, dependency injection, error handling, logging, validation and test patterns.
- Reuse existing components and libraries before adding dependencies.
- Avoid introducing packages, infrastructure or architectural patterns without a clear need.
- Never hardcode secrets, credentials, environment-specific endpoints or personal data.
- Validate inputs and enforce authorization on the server side where applicable.
- Handle failure paths, cancellation, retries and idempotency where relevant.
- Keep public contracts backward-compatible unless the plan explicitly approves a breaking change.
- Add/update tests with the code. Do not weaken or delete tests merely to make a build pass.
- Do not claim tests passed unless they were actually run and their result observed.
- Do not commit, push, deploy, alter production data or perform destructive operations unless explicitly authorized.

## Required workflow

### 1. Restate the slice

Identify:
- feature/task IDs and titles
- linked PRD requirement IDs
- acceptance criteria
- dependencies
- expected files/modules
- definition of done

### 2. Inspect before changing

Trace the existing request/data flow and relevant code. Identify the smallest safe implementation point. Check for existing APIs, services, components, database objects and tests.

### 3. Resolve design questions

Use the software architect skill for cross-cutting design or contract questions; backend architect for server/data/API design; senior developer for implementation practices. Record significant decisions in the project's decision log/ADR.

If the implementation reveals a material scope or architecture gap, pause and propose a plan change instead of silently expanding scope.

### 4. Implement incrementally

Make focused changes in logical steps:
- contracts/models and validation
- business logic
- persistence/integration
- API/UI wiring
- error handling and telemetry
- tests and documentation

The exact order depends on the repository. Do not create unnecessary layers or files solely to match this illustrative sequence.

### 5. Verify

Run relevant checks available in the repository:
- formatter/linter/static analysis
- build/type checking
- focused unit tests
- integration/contract tests
- broader test suite when practical

Inspect the diff for accidental changes, secrets, debug code, generated artifacts and unrelated modifications.

If a check cannot be run, report it as `Not Run` with the reason. If it fails, report the exact failure and do not label the task complete.

### 6. Update evidence and status

Record:
- files/modules changed
- implementation summary
- tests/checks and actual results
- acceptance criteria evidence
- known limitations
- follow-up tasks or blockers

Update the task board only to the status supported by evidence. A completed coding task may be `In Review`; do not set the whole feature to `Done` until all feature acceptance criteria and review gates pass.

## Definition of Done

A task is `Done` only when:
- its planned deliverable is implemented
- its acceptance criteria are satisfied
- relevant tests are added/updated and pass, or an approved exception is documented
- code follows repository standards
- security, error handling and observability are addressed where relevant
- documentation/configuration/migration work is complete where applicable
- no unresolved blocker remains for that task
- evidence is recorded in the project artifacts

A feature is `Done` only when all required tasks are complete, feature acceptance criteria pass, and independent review is approved.

## Output

Summarize:
1. work item IDs implemented
2. key files changed
3. behaviour delivered
4. tests/checks run and results
5. acceptance criteria met/not met
6. blockers, risks and follow-up work
7. task board status changes
8. next recommended task

Never claim completion based only on code generation.
