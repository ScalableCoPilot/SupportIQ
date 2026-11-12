---
name: implementation-review
description: Performs an evidence-based review of an implemented feature against the approved PRD, feature acceptance criteria, architecture and engineering quality gates. Use before marking a feature Done.
---

# Implementation Review

## Mission

Independently verify that a feature is correct, secure, maintainable, tested and aligned with approved scope. Review the actual diff and evidence; do not assume the implementation skill completed every requirement.

## Review inputs

Read:
- approved PRD and requirement traceability
- approved implementation plan and feature specification
- relevant task board entries
- project instructions and applicable architecture/developer skills
- source diff, tests, build output and CI results
- relevant ADRs, security/privacy requirements and migration notes

## Review checklist

### Functional and traceability
- Every acceptance criterion is implemented and evidenced.
- Behaviour matches approved requirements.
- Validation, boundary cases and failure paths are handled.
- No unapproved scope changes or hidden business-rule assumptions exist.

### Architecture and maintainability
- Change fits established architecture and repository conventions.
- Responsibilities and dependencies are appropriate.
- No unnecessary abstractions, duplication or unrelated refactoring.
- Public contracts and compatibility are considered.

### Security and privacy
- Authentication and authorization are correct.
- Input validation and output encoding are appropriate.
- Secrets and sensitive data are not exposed in source, logs or errors.
- Data access follows least privilege and safe query practices.
- Relevant threat/privacy concerns are addressed.

### Reliability and operations
- Errors are handled consistently.
- Logging/metrics/tracing are useful and do not leak sensitive values.
- Retry, timeout, cancellation and idempotency are appropriate where relevant.
- Configuration, migrations, deployment and rollback are covered where applicable.

### Testing
- Tests cover normal, boundary and failure cases.
- Tests are meaningful and not weakened to pass.
- Relevant automated checks were actually executed.
- Gaps and unrun checks are explicitly documented.

### Delivery hygiene
- No accidental files, debug statements, credentials or unrelated changes.
- Documentation and configuration are updated.
- Acceptance evidence is linked from the review record.

## Finding severity

- `Critical`: exploitable security issue, data loss/corruption, severe outage or fundamental requirement failure.
- `High`: major incorrect behaviour, authorization failure, broken integration or important acceptance criterion failure.
- `Medium`: material defect with workaround or significant maintainability/reliability concern.
- `Low`: minor defect, clarity or non-blocking improvement.
- `Info`: observation or suggestion, not a defect.

Each finding must include location, evidence, impact and a recommended correction. Do not report speculative concerns as confirmed defects.

## Review decision

Use one:
- `Approved`: required criteria pass; feature may proceed to completion/acceptance.
- `Changes Requested`: one or more blocking findings remain.
- `Pending Evidence`: required tests, CI or acceptance evidence is missing.
- `Not Reviewed`: insufficient context to perform a reliable review.

Do not change code during a review unless the user explicitly asks you to fix findings. If asked to fix, implement only agreed findings, rerun relevant checks and review the changed diff.

## Review record

Save under `docs/implementation/reviews/FEAT-XXX-review.md`:

```markdown
# Feature Review – FEAT-XXX

- Date:
- Reviewer:
- PR/commit:
- Decision:
- Scope reviewed:

## Acceptance criteria
| Criterion | Result | Evidence |
|---|---|---|

## Findings
| ID | Severity | Location | Finding | Required action |
|---|---|---|---|---|

## Checks
| Check | Result | Notes |
|---|---|---|

## Residual risks / limitations

## Follow-up tasks
```

## Output

Summarize decision, blocking findings, tests/evidence checked, residual risks and whether the feature can be marked `Done`. Update the task board only when the evidence supports the change.
