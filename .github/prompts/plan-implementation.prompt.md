---
mode: agent
description: Create a dependency-aware implementation plan from the approved PRD.
---

Use the `implementation-planning` skill.

1. Find and verify the approved PRD and related requirement/baseline artifacts.
2. Read repository instructions and relevant architecture skills.
3. Inspect the existing repository and identify its actual technology stack.
4. Create epics → features → tasks → subtasks with stable IDs, requirement traceability, acceptance criteria, dependencies, estimates, risks and test tasks.
5. Create/update `docs/implementation/implementation-plan.md` and `docs/implementation/feature-task-board.md`.
6. Validate coverage, dependencies and completeness.
7. Leave the plan as `Draft – Pending Approval`. Do not implement code.

If the approved PRD cannot be confirmed, stop and ask.
