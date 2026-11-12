# SupportIQ Feature and Task Board

> Approved companion to the [implementation plan](implementation-plan.md). The project owner approved the plan, authorized implementation under DEC-042, approved the application stack under DEC-041, Vite tooling under DEC-043, modular-monolith architecture under DEC-044, Azure AI Search under DEC-045, Azure Blob Storage under DEC-046, Azure development storage for local Blob access under DEC-047, Azure Function/Service Bus document processing under DEC-048, a dedicated development Service Bus namespace under DEC-049, EF Core under DEC-050, JWT renewal/revocation behavior under DEC-051/DEC-052, single-tenant internal membership under DEC-053, email sign-in under DEC-054, and the 10,000,000-byte upload threshold under DEC-055. Other open design/service decisions remain gated.

## Status definitions

`Not Started` · `Ready` · `In Progress` · `Blocked` · `In Review` · `Done` · `Deferred` · `Cancelled`

## Summary

- Plan version: 1.4
- Last reconciled: 2026-11-12
- Plan status: `Approved`
- Active features: 12
- Planned tasks: 45
- Features in progress: 1
- Tasks done: 2
- Tasks in progress: 2
- Implementation started: Yes
- Work in progress: TASK-002 (API/data/auth contracts), TASK-003 (remaining service/configuration decisions)
- Blocked decisions: Technical/service choices and other open questions listed in the plan

## Feature board

| Feature ID | Epic ID | Feature | PRD IDs | Priority | Estimate | Status | Dependencies | Acceptance evidence |
|---|---|---|---|---|---|---|---|---|
| FEAT-001 | EPIC-001 | Approved technical baseline and detailed contracts | BR-001, BR-004, API-001, AI-004, FR-OP-12–14 | Must / prerequisite | M | In Progress | None | Owner-approved decision/contract records |
| FEAT-002 | EPIC-001 | Identity, authentication, and tenant authorization | FR-CA-14, FR-OP-10–11, FR-OP-14, API-001, RULE-010–015, AC-001, AC-004, AC-007, AC-010 | Must | L | Not Started | FEAT-001 | Claims, authorization and negative API tests |
| FEAT-003 | EPIC-001 | Tenant membership management | FR-OP-09, ROLE-001, RULE-013, AC-006, US-002 | Must | M | Not Started | FEAT-002 | Membership/audit integration tests |
| FEAT-004 | EPIC-002 | Knowledge document ingestion and retention | FR-KB-01–08, FR-KB-17, DATA-002, AC-009–010, AC-014 | Must | XL | Not Started | FEAT-001, FEAT-002 | 10,000,000-byte per-file validation, ingestion, failure, reprocess and deletion tests |
| FEAT-005 | EPIC-002 | Knowledge authoring and external publication governance | FR-KB-09–16, RULE-009, RULE-016–024, AC-001, AC-003, AC-008 | Must | L | Not Started | FEAT-002, FEAT-004 | Lifecycle and role-boundary tests |
| FEAT-006 | EPIC-003 | Permission-scoped RAG and grounded answers | FR-CA-01–13, AI-001, AI-004, AC-001–002, AC-010 | Must | XL | Not Started | FEAT-001, FEAT-002, FEAT-004, FEAT-005 | Scope, citation, abstention and failure tests |
| FEAT-007 | EPIC-003 | Isolated assistant conversations and history | FR-CA-09, FR-CA-14–15, RULE-014–015, AC-004, US-005 | Must | M | Not Started | FEAT-002, FEAT-006 | Cross-account/tenant history tests |
| FEAT-008 | EPIC-003 | Human escalation and agent response | FR-CA-12, FR-CA-16, AC-005, US-006 | Must | M | Not Started | FEAT-003, FEAT-007 | Escalation end-to-end tests |
| FEAT-009 | EPIC-004 | Platform operations metadata boundary | ROLE-004, RULE-010–011, AC-007, US-007 | Must | M | Not Started | FEAT-001, FEAT-002 | Platform metadata allow/deny tests |
| FEAT-010 | EPIC-005 | Synthetic assets and AI/RAG evaluation | BR-001, BR-003, DATA-003, AI-002, AC-010, AC-012 | Must for release readiness | L | Not Started | FEAT-006 | Repeatable RAG, API, tenant-isolation and structured-output evidence |
| FEAT-011 | EPIC-005 | English-only UI and basic accessibility | NFR-007, NFR-011, AC-011 | Must | M | Not Started | FEAT-001 and user-facing features | Keyboard, screen-reader, labels and contrast checks |
| FEAT-012 | EPIC-004 | Reproducible local and hosted Azure demonstration | BR-001, BR-004, FR-OP-12–13, AC-013 | Must for release readiness | L | Not Started | FEAT-001–FEAT-011 | Local/hosted setup, security and release evidence |

## Task board

Estimates use relative T-shirt sizes; they are not durations or commitments. Owner roles are role-level suggestions, not named assignments. Verification describes required evidence, not tests already run.

| Task ID | Feature ID | Task / deliverable | Type | Priority | Estimate | Status | Depends on | Owner role | Verification / evidence |
|---|---|---|---|---|---|---|---|---|---|
| TASK-001 | FEAT-001 | Confirm proposed application stack, architecture boundaries, and technology decisions that require owner approval. | Design / decision | Must | M | Done | — | Project owner / architect | Application stack, modular-monolith boundary, persistence technology, search/storage/processing services, token renewal/revocation, tenant membership cardinality, and email sign-in are recorded under DEC-041–DEC-054; exact Foundry model/deployment and resource configuration remain open under TASK-003. |
| TASK-002 | FEAT-001 | Define the detailed API, data, identity, authorization, error, and deletion contracts without changing approved invariants. | Design / contract | Must | L | In Progress | TASK-001 | Architect / backend developer | Draft contract in `docs/architecture/api-contracts.md`; traces to API-001, AC-010, active-membership authorization, and source/derived deletion requirements; review remains open. |
| TASK-003 | FEAT-001 | Resolve Azure Search, file storage, background processing, Foundry deployment, local/hosted resource, and configuration options. | Design / dependency | Must | L | In Progress | TASK-001 | Project owner / cloud architect | Azure AI Search, Azure Blob Storage, and Azure Function/Service Bus processing selected under DEC-045–DEC-048; dedicated dev namespace selected under DEC-049; account/configuration remain unverified; no resource provisioned. |
| TASK-004 | FEAT-002 | Implement Azure-SQL-backed identity and JWT issuance with required claims and configurable expiry/renewal/revocation. | Backend | Must | L | Not Started | TASK-002, TASK-003 | Backend developer | Authenticated API tests verify required claims and configured token behavior. |
| TASK-005 | FEAT-002 | Enforce server-derived tenant scope, active membership, and role authorization at protected application boundaries. | Backend / security | Must | L | Not Started | TASK-004 | Backend developer | Negative tests reject tenant-header/parameter switching and unauthorized role/membership access. |
| TASK-006 | FEAT-002 | Implement the approved internal/external sign-in and session UI for the selected frontend. | Frontend | Must | M | Not Started | TASK-004 | Frontend developer | UI uses authenticated identity and provides observable success/error states. |
| TASK-007 | FEAT-002 | Add authentication, tenant-isolation, customer-history, and Platform Admin access-boundary tests. | Test / security | Must | M | Not Started | TASK-005, TASK-006 | QA / security reviewer | Automated negative and positive test evidence for AC-001, AC-004, AC-007, AC-010. |
| TASK-008 | FEAT-003 | Implement tenant membership invitation/provisioning, updates, role assignment, and immediate deactivation/removal. | Backend | Must | M | Not Started | TASK-004, TASK-005 | Backend developer | API behavior follows the approved Tenant Admin and explicitly authorized higher-role boundaries. |
| TASK-009 | FEAT-003 | Implement the Tenant Admin membership-management UI. | Frontend | Must | M | Not Started | TASK-008 | Frontend developer | Authorized user can manage membership; unauthorized actions are unavailable and denied server-side. |
| TASK-010 | FEAT-003 | Audit membership changes and test active-membership access and cross-tenant restrictions. | Backend / test | Must | M | Not Started | TASK-008, TASK-009 | Backend developer / QA | Audit record and membership authorization tests satisfy AC-006. |
| TASK-011 | FEAT-004 | Implement document upload, 10 MB per-file maximum validation, metadata, source storage, and visible processing state. | Backend / data | Must | L | Not Started | TASK-002, TASK-003, TASK-005 | Backend developer | Accept files up to 10,000,000 bytes and reject larger files; test below, at, and above the limit, plus invalid files. |
| TASK-012 | FEAT-004 | Implement extraction, normalization, chunking, embedding, indexing, retry/failure status, and authorized reprocessing. | Backend / integration | Must | XL | Not Started | TASK-011 | Backend developer | Processing success/failure, retry, and reprocess evidence for selected services. |
| TASK-013 | FEAT-004 | Implement document-status, processing-error, and reprocess UI states. | Frontend | Must | M | Not Started | TASK-011, TASK-012 | Frontend developer | User can distinguish pending, successful, and failed processing without a success-shaped fallback. |
| TASK-014 | FEAT-004 | Implement 90-day source/derived-content deletion; define backup and log/evaluation retention only after owner decisions. | Backend / data lifecycle | Must | L | Not Started | TASK-012 | Backend developer / project owner | Expiry tests verify source, extracted text, chunks, and embeddings are deleted; unresolved retention is recorded. |
| TASK-015 | FEAT-004 | Add ingestion, validation, failure, update/reprocess, stale-index, and retention integration tests. | Test | Must | L | Not Started | TASK-011–TASK-014 | QA / backend developer | Reproducible test evidence covers normal and failure paths. |
| TASK-016 | FEAT-005 | Implement tenant-scoped internal knowledge and external-article author/edit workflows. | Backend / frontend | Must | L | Not Started | TASK-005, TASK-011 | Backend and frontend developers | Tenant Admin and Support Agent authoring works without review/publish authority. |
| TASK-017 | FEAT-005 | Implement review, approve, reject, publish, and withdraw transitions with role checks and audit history. | Backend | Must | L | Not Started | TASK-016 | Backend developer | State-transition tests enforce Support Manager/authorized-role boundary. |
| TASK-018 | FEAT-005 | Implement review-date overrides, 90-day default, stale triggers, and withdrawal from external retrieval. | Backend / scheduling | Must | M | Not Started | TASK-017 | Backend developer | Expiry, report, inaccuracy, product/process-change, manual-flag, and reapproval tests. |
| TASK-019 | FEAT-005 | Add end-to-end knowledge lifecycle and external-publication authorization tests. | Test / security | Must | M | Not Started | TASK-016–TASK-018 | QA / security reviewer | AC-001, AC-003, AC-008 evidence, including cross-tenant and stale-content denial. |
| TASK-020 | FEAT-006 | Implement permission-filtered retrieval over selected indexed knowledge. | Backend / AI | Must | L | Not Started | TASK-005, TASK-012, TASK-017 | Backend / AI developer | Results are limited to active tenant, role, permission, and external publication scope. |
| TASK-021 | FEAT-006 | Implement grounded generation, source references, and abstention for insufficient, conflicting, or stale evidence. | AI / backend | Must | XL | Not Started | TASK-020 | AI / backend developer | Citation traceability and abstention cases pass; Foundry model/deployment is recorded. |
| TASK-022 | FEAT-006 | Implement internal and external assistant UI with citations, abstention, and failure states. | Frontend | Must | L | Not Started | TASK-006, TASK-021 | Frontend developer | User sees source references and clear unsupported/failure responses. |
| TASK-023 | FEAT-006 | Add retrieval, prompt-injection, authorization, citation, abstention, and dependency-failure tests. | Test / security | Must | L | Not Started | TASK-020–TASK-022 | QA / security reviewer | Negative cases confirm untrusted documents cannot override system instructions or scope. |
| TASK-024 | FEAT-007 | Implement authenticated conversation/message persistence and retrieval. | Backend / data | Must | M | Not Started | TASK-004, TASK-005, TASK-021 | Backend developer | Authenticated users can create and retrieve only permitted conversation records. |
| TASK-025 | FEAT-007 | Enforce per-account and tenant conversation-history isolation. | Backend / security | Must | M | Not Started | TASK-024, TASK-005 | Backend developer | Cross-account, cross-tenant, and internal/external history requests are denied. |
| TASK-026 | FEAT-007 | Implement assistant conversation/history UI for approved internal and external audiences. | Frontend | Must | M | Not Started | TASK-022, TASK-024, TASK-025 | Frontend developer | UI displays only server-authorized history and provides safe empty/error states. |
| TASK-027 | FEAT-007 | Obtain owner decision on external conversation-history retention/deletion, then implement the approved lifecycle. | Decision / data lifecycle | Must | M | Not Started | TASK-001, TASK-024 | Project owner / backend developer | Decision recorded before lifecycle behavior is implemented; no retention period assumed. |
| TASK-028 | FEAT-008 | Implement unanswered-question escalation and its authorized support workflow. | Backend | Must | M | Not Started | TASK-008, TASK-024 | Backend developer | Escalated conversation is available to authorized Support Agents only. |
| TASK-029 | FEAT-008 | Implement Support Agent view/respond UI for escalated external conversations. | Frontend | Must | M | Not Started | TASK-026, TASK-028 | Frontend developer | Agent can respond to escalated item without exposing unrelated histories. |
| TASK-030 | FEAT-008 | Add end-to-end escalation, agent response, and customer-isolation tests. | Test / security | Must | M | Not Started | TASK-025, TASK-027–TASK-029 | QA / security reviewer | AC-005 and isolation evidence across customer and agent roles. |
| TASK-031 | FEAT-009 | Define and implement allowlisted platform-level operational metadata access. | Backend / security | Must | M | Not Started | TASK-002, TASK-005 | Backend developer | Fields and queries are limited to approved platform-level metadata. |
| TASK-032 | FEAT-009 | Implement platform health/status/usage views within the approved metadata boundary. | Frontend / operations | Must | M | Not Started | TASK-031 | Frontend developer / platform implementer | Platform Admin can inspect permitted metadata but no tenant business content. |
| TASK-033 | FEAT-009 | Add negative tests proving operational views/APIs do not expose tenant content or customer data. | Test / security | Must | M | Not Started | TASK-031, TASK-032 | QA / security reviewer | Leak-oriented tests satisfy AC-007 and RULE-010–RULE-011. |
| TASK-034 | FEAT-010 | Create fabricated organizations, users, knowledge, and first-release evaluation assets. | Test data | Must | M | Not Started | TASK-001, TASK-005 | QA / data owner | Data review confirms no real customer data, secrets, or deferred ticket taxonomy. |
| TASK-035 | FEAT-010 | Define and obtain approval for evaluation datasets, measurable metrics, and thresholds. | AI evaluation / decision | Must before release | L | Not Started | TASK-021, TASK-034 | Project owner / AI evaluator | Approved criteria cover retrieval, grounding, citations, structured outputs, tenant isolation, core API invariants, abstention, and prompt injection. |
| TASK-036 | FEAT-010 | Build repeatable evaluation execution and capture model, prompt, deployment, and run metadata. | Test / AI evaluation | Must | L | Not Started | TASK-035 | AI developer / QA | Repeated runs create comparable, traceable evidence without inventing success thresholds. |
| TASK-037 | FEAT-010 | Execute approved evaluations and summarize results, limitations, and release-gate evidence. | Test / release | Must before release | M | Not Started | TASK-007, TASK-023, TASK-033, TASK-036 | QA / project owner | Results include RAG and structured-output evaluation plus tenant-isolation/core-API evidence; failures and limitations remain visible. |
| TASK-038 | FEAT-011 | Apply English-only content and basic accessibility practices across implemented user-facing flows. | Frontend / accessibility | Must | L | Not Started | TASK-001, TASK-022, TASK-026, TASK-029, TASK-032 | Frontend developer | Keyboard access, readable contrast, labels, and screen-reader-friendly controls are present. |
| TASK-039 | FEAT-011 | Perform keyboard, screen-reader, and contrast review; record findings and fixes without asserting an unapproved WCAG level. | Test / accessibility | Must | M | Not Started | TASK-038 | QA / accessibility reviewer | Review evidence covers implemented first-release flows and remaining limitations. |
| TASK-040 | FEAT-012 | Create reproducible local configuration and setup for the selected application and Azure SQL. | Dev environment | Must | M | Not Started | TASK-003 | Developer / data engineer | Clean local setup and test instructions work without repository secrets. |
| TASK-041 | FEAT-012 | Configure and deploy the hosted Azure demo using owner-approved resources and secure configuration. | Deployment | Must | L | Not Started | TASK-003, TASK-007, TASK-010, TASK-015, TASK-019, TASK-023, TASK-030, TASK-033, TASK-037, TASK-039, TASK-040, TASK-042 | Cloud implementer | Deployment and smoke/access-boundary checks pass; no unapproved resources are provisioned. |
| TASK-042 | FEAT-012 | Implement monitoring, safe structured telemetry, secret handling, and available cost controls. | Operations / security | Must | L | Not Started | TASK-031, TASK-040 | Platform implementer | Telemetry is useful and does not expose credentials or tenant content; cost controls are documented. |
| TASK-043 | FEAT-012 | Obtain measurable service targets and run performance/reliability tests against approved values. | Test / operations | Must before release | L | Not Started | TASK-012, TASK-021, TASK-036, TASK-041 | Project owner / QA / platform implementer | Owner-approved latency, availability/recovery, concurrency, and cost targets plus test results. |
| TASK-044 | FEAT-012 | Complete release checklist, setup/deployment/test documentation, and hosted-demo verification. | Documentation / release | Must before release | M | Not Started | TASK-037, TASK-039, TASK-041–TASK-043 | Release owner / project owner | Reproducibility, synthetic-data, security, evaluation, operational, and known-limitations evidence reviewed. |
| TASK-045 | FEAT-001 | Create the initial .NET 10 API and React + TypeScript frontend solution scaffold with Vite, baseline build scripts, and local run instructions. | Foundation / setup | Must | M | Done | DEC-041, DEC-043 | Developer | `dotnet build`, frontend production build/lint, and API `/health` smoke test passed; no unapproved Azure services or secrets were added. |

## Subtasks

No separate subtasks are proposed in this draft; each task is already a bounded deliverable with verification criteria. Add stable `SUB-###` items only if decomposition is needed after plan approval.

## Blockers and decisions

| ID | Affected work item | Blocker / decision | Next action | Owner role | Status |
|---|---|---|---|---|---|
| Q-007 / API-002 | TASK-003, TASK-012, TASK-021, TASK-041 | Azure AI Search, Blob Storage, and Function/Service Bus are selected; AI models/region/cost and local storage/queue account availability/configuration remain unverified, as do resource provisioning and detailed integration configuration. | Resolve remaining integration choices and approve resources/configuration before dependent implementation or provisioning. | Project owner | Partially answered |
| Q-026 | TASK-002, TASK-004 | Access-token expiry must be configurable, but its duration is not chosen. | Require explicit secure configuration; do not invent a lifetime/default. | Project owner | Open |
| Q-010 | TASK-014, TASK-042 | Backup and log/evaluation-record retention remain open. | Decide lifecycle policy; do not weaken approved source/derived deletion. | Project owner | Partially answered |
| Q-025 | TASK-027, TASK-030 | External conversation retention/deletion remains unresolved. | Record the policy before implementing conversation lifecycle. | Project owner | Open |
| Q-011 / Q-012 | TASK-035–TASK-037, TASK-043 | Evaluation and service targets must be measurable but no values are approved. | Define and approve criteria before release approval; do not invent values. | Project owner | Open |
| Q-014 | TASK-039 | WCAG conformance level remains unresolved. | Apply approved basic practices; decide conformance claim separately. | Project owner | Open |
| Remaining architecture/service decisions | TASK-001–TASK-003 | Exact API/data/auth contracts, local storage/Service Bus account availability, Foundry deployment/configuration, and Azure resource details remain open. | Resolve owner decisions before dependent feature work or resource provisioning; selected services are not provisioned. | Project owner / architect | Open |

## Evidence and notes

- Requirement and acceptance-criteria mappings are in the [approved PRD](../requirements/approved/PRD.md) and [requirements traceability](../requirements/analysis/requirements-traceability.md).
- Implementation authorization is recorded as DEC-042 / EV-068. TASK-045 and TASK-001 are complete; TASK-002 and TASK-003 are in progress.
- Open design/service decisions still gate dependent feature work and all Azure resource provisioning.
