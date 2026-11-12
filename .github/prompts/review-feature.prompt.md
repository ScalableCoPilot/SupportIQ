---
agent: agent
description: Review a feature against approved requirements and engineering quality gates.
---

Use the `implementation-review` skill.

Target feature: ${input:featureId:Enter a feature ID, for example FEAT-001}

Review the actual diff, approved PRD, feature acceptance criteria, tests and architecture. Record findings with severity and evidence in `docs/implementation/reviews/`. Return Approved, Changes Requested or Pending Evidence. Do not modify code unless explicitly asked.
