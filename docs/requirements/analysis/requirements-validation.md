# SupportIQ Requirements Validation — Gate 3 Review

## Status

This is the validation record for the Gate 3-approved requirements package. The project owner approved the package as presented. Requirements explicitly marked Approved at Gate 3 are approved; baseline-only statements retained as Draft/unprioritized and unresolved/deferred decisions retain those statuses. The PRD was subsequently approved at Gate 4 with Q-033 remaining open.

## Review results

| Validation area | Result | Evidence / remaining work |
|---|---|---|
| Source preservation | Pass | Original [baseline](../baseline/SupportIQ-Baseline.md) remains unchanged; source statements are treated as evidence rather than approval. |
| Stakeholders and roles | Pass with deferred details | Internal staff, external customers, Tenant Admins, Support Agents, Support Managers, and Platform Admin boundaries are recorded. Detailed registration, invitation, approval, and restriction-assignment workflows remain deferred. |
| Scope and exclusions | Approved with residual Draft items | Knowledge Management with RAG is the approved first-release vertical slice. Ticket list/detail, classification/summary, dashboard/analytics, lookup tools, ticket data taxonomy/fields/seed strategy, and issue/PR/CI/delivery workflow requirements are explicitly deferred. Other baseline capabilities remain Draft and must not be assumed in or out of scope. |
| Requirement identification and status | Pass with explicit residual Draft items | Stable IDs and source references are maintained. Stakeholder-confirmed requirements approved at Gate 3 are marked accordingly. Baseline-only items explicitly retained as Draft/unprioritized are not promoted into the approved scope. |
| Security and privacy | Pass with design items | Authentication, server-derived tenant scope, role-based authorization, external knowledge eligibility, customer history isolation, Platform Admin prohibition, and membership audit boundaries are captured. Registration/verification, token lifecycle details, and some permission-assignment workflows remain deferred. |
| Data lifecycle | Partial | The 90-day period starts on original upload; source documents, extracted text, chunks, and embeddings are deleted after expiry. Backup deletion and log/evaluation-record retention remain open. Customer conversation-history retention/deletion also remains deferred. |
| AI/RAG | Partial | Azure AI Foundry is selected for generation and embeddings. Exact models, region, deployment configuration, and AI cost envelope remain deferred. Measurable evaluation datasets, metrics, and thresholds must be defined during detailed design before release approval. |
| Non-functional requirements | Partial | English-only and basic accessibility practices are confirmed. WCAG level and numeric latency, availability/recovery, concurrency, and operating-cost targets remain unresolved; the owner directed measurable targets to detailed design/performance testing before release approval. |
| API and integration | Partial | Requirements-level authentication, tenant isolation, role authorization, secure knowledge access, and consistent source/derived deletion are confirmed. Endpoint paths, schemas, validation details, pagination, idempotency, and error formats are deferred to solution/detailed design. Other resource/configuration dependencies remain in the risk/dependency register. |
| Traceability and acceptance | Pass for Gate 3 package | User stories, acceptance criteria, and mappings in [requirements-traceability.md](requirements-traceability.md) were approved at Gate 3. Test-case IDs and executable test designs remain for later test planning. |
| Prioritization | Partial | The owner confirmed the first-release vertical slice and explicit deferrals. A full priority ranking for remaining baseline-derived requirements has not been approved; do not infer one. |

## Approved scope and priority at Gate 3

| Disposition | Capabilities | Basis / status |
|---|---|---|
| Must-have first-release slice | Knowledge Management with a RAG-based assistant; internal and external audiences; permission-scoped retrieval; external knowledge review/approval/publication; human escalation; the confirmed role and tenant boundaries. | Explicitly selected and approved as part of the Gate 3 requirements package. |
| Deferred from first release | Ticket list/detail, ticket summary/classification, simple dashboard/analytics, read-only ticket/customer lookup, synthetic ticket taxonomy/fields/seed strategy, and GitHub issue/PR, CI, and delivery workflow requirements. | Explicit owner deferrals; workflow requirements are for the next phase, ticket data definition for a future phase. |
| Unprioritized baseline items | Remaining baseline capabilities not included in the approved slice or named deferrals. | Keep Draft and do not infer inclusion or exclusion. |

## Deferred and unresolved items for Gate 3 visibility

The following items are not silently treated as resolved or approved:

- Document backup deletion and log/evaluation-record retention, plus external-customer conversation-history retention/deletion.
- Exact AI models, region, deployment configuration, and AI cost envelope.
- AI/RAG evaluation datasets, measurable metrics, and acceptance thresholds.
- Numeric latency, availability/recovery, concurrency, and operating-cost targets.
- WCAG conformance level.
- Detailed API schemas, paths, validation behavior, pagination, idempotency, and error formats.
- Registration/verification and invitation/approval workflows, and detailed role-restriction assignment.
- GitHub issue/PR, CI, and delivery workflow scope, which the owner deferred to the next phase.

The package distinguishes items deferred to detailed design from items deferred to a future project phase. The recorded timing/acceptance conditions were approved as part of the Gate 3 package; the numeric values and detailed design outputs listed above remain unresolved until their stated stage.

## Gate 3 approval outcome

The project owner approved the Gate 3 requirements package as presented and subsequently approved the [PRD](../approved/PRD.md) at Gate 4 with Q-033 remaining open. Approved requirements and traceability are recorded in [requirements-inventory.md](requirements-inventory.md) and [requirements-traceability.md](requirements-traceability.md). Items explicitly retained as Draft/unprioritized and unresolved or deferred remain in those states. Implementation planning requires separate Gate 5 authorization.
