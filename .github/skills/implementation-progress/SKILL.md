---
name: implementation-progress
description: Audits and updates implementation progress using the plan, task board, repository state, tests and review evidence. Use at the start/end of implementation sessions, after task completion, or when asked for project status.
---

# Implementation Progress

## Mission

Maintain a truthful, current and auditable view of delivery progress. This skill reconciles documented status with evidence in the repository; it does not infer progress from chat history or optimistic assumptions.

## Sources of truth

Use this precedence:
1. approved PRD for business scope
2. approved implementation plan for planned scope and dependencies
3. task board for current work-item status
4. source code, tests, build output, CI results and review records for completion evidence
5. progress log for dated history

If sources conflict, do not silently choose one. Record the conflict and ask the owner to resolve it.

## Required workflow

### 1. Load project state

Read:
- approved PRD and implementation plan
- feature/task board
- latest progress log entry
- relevant review records and decisions
- repository branch and working-tree state
- available test/CI evidence

### 2. Reconcile every changed item

For each work item being updated, check:
- Is the implementation present?
- Are the relevant tests present and passing?
- Are acceptance criteria evidenced?
- Are dependencies complete?
- Is review complete?
- Is there a blocker or unresolved decision?

Set status based on evidence:

| Status | Meaning |
|---|---|
| `Not Started` | No work has begun |
| `Ready` | Scope and dependencies are clear; eligible to start |
| `In Progress` | Work has demonstrably started |
| `Blocked` | Cannot proceed; blocker and owner/action are recorded |
| `In Review` | Implementation is submitted for review; not yet accepted |
| `Done` | Definition of Done and required review/acceptance evidence are satisfied |
| `Deferred` | Intentionally moved out of current delivery scope with approval |
| `Cancelled` | Explicitly cancelled by an authorized owner |

Do not mark an item `Done` because files exist or code appears complete. Do not automatically change statuses for unrelated items.

### 3. Calculate progress transparently

Report counts by status at epic, feature and task levels.

If showing a percentage:
- state the denominator and method
- use a consistent unit (prefer weighted task estimates if estimates exist; otherwise show simple task-count completion)
- exclude `Deferred` and `Cancelled` from the active-scope denominator, but report them separately
- never average feature percentages without explaining weighting
- do not present a percentage as a measure of business value

Recommended formula for simple task-count progress:

`Done active tasks / (all active tasks) × 100`

Also show blocked count and overdue items only when due dates are explicitly recorded.

### 4. Identify delivery health

Highlight:
- critical-path tasks and dependency delays
- blocked items, reason, owner role and next action
- features at risk
- requirements without implementation coverage
- tasks in progress for an unusually long period, only if dates are available
- missing tests/review evidence
- scope changes and newly discovered work
- decisions needed from product/architecture/security stakeholders

Do not invent owners, dates, estimates or causes.

### 5. Update artifacts

Update:
- `docs/implementation/feature-task-board.md` for verified status changes
- `docs/implementation/progress-log.md` with a dated, concise change record
- feature specs/review records only when new evidence belongs there

Keep a history. Do not erase previous progress entries. If the date cannot be reliably established from the environment, ask or omit the date rather than inventing it.

### 6. Recommend next action

Choose the next task by:
1. unblock critical-path work
2. satisfy prerequisites
3. reduce high-impact uncertainty/risk
4. complete the current vertical slice
5. continue by approved business priority

Explain why this is the next action. Do not start implementation unless asked.

## Progress log entry format

```markdown
## YYYY-MM-DD – Progress update

- Branch/commit:
- Summary:
- Work items changed:
  - TASK-001: In Progress → Done — evidence:
- Tests/CI:
- Blockers:
- Decisions required:
- Scope changes:
- Next recommended action:
```

## Output format

Provide:
1. overall status and calculation method
2. epic/feature/task counts by status
3. completed work with evidence
4. in-progress and blocked work
5. requirement coverage gaps
6. risks/decisions
7. next recommended action
8. artifacts updated

If no reliable evidence is available, say so and leave the status unchanged.
