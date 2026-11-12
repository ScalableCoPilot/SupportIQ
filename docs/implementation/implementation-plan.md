# SupportIQ Implementation Plan

| Field | Value |
|---|---|
| Plan version | 1.4 |
| Plan status | `Approved` |
| PRD | [Approved PRD](../requirements/approved/PRD.md), Gate 4; Q-033 resolved under DEC-040 |
| Gate 5 | Authorized by project owner on 2026-11-12 for planning only; DEC-038 / EV-064 |
| Prepared on | 2026-11-12 |
| Repository baseline | `main` at `cac01d5296b92a6d4d7b93610a128ba65d388b53` |
| Implementation status | Authorized by DEC-042; scaffold complete; detailed contracts are in progress |

The project owner approved this plan on 2026-11-12. Implementation was separately authorized under DEC-042; that authorization does not resolve open requirements/design decisions or authorize Azure resource provisioning.

## 1. Scope and objectives

### In scope

Plan the approved first demonstrable release: tenant-safe knowledge ingestion and lifecycle management, external-article review and publication, grounded RAG for internal support staff and external customers, customer conversation isolation, human escalation, tenant membership, restricted platform operations, English-only/basic-accessibility practices, synthetic data, evaluation, and a hosted Azure demonstration after local development and testing.

### Out of scope

- Ticket list/detail, ticket summarization/classification, advanced ticket intelligence, dashboards/analytics, and read-only ticket/customer lookup.
- Synthetic ticket taxonomy, fields, and seed strategy; additional agent-copilot and workflow-tool capabilities.
- GitHub issue/PR and CI/delivery workflow requirements, which are deferred by the approved PRD.
- Unapproved or Draft/unprioritized baseline capabilities and any requirement not included in the Gate 4-approved first-release scope.
- Code implementation, deployment, or Azure resource provisioning as part of this planning task.

### Constraints

- Use fabricated data only. Preserve the tenant, role, customer-conversation, and platform-admin boundaries in the PRD.
- Preserve the approved 90-day document-retention rule: delete the source document, extracted text, chunks, and embeddings from the system after expiry.
- Enforce the owner-confirmed maximum upload size of 10 MB per file (FR-KB-17 / AC-014).
- Azure SQL for local and hosted environments and Azure AI Foundry for generation and embeddings are approved. Other named services and their configurations are not.
- The PRD's unresolved decisions, Draft requirements, and explicitly deferred features retain their status.

## 2. Repository and technical baseline

| Area | Discovered state |
|---|---|
| Application code | Initial .NET 10 API and React + TypeScript/Vite scaffold exists under `src\backend` and `src\frontend`. |
| Build/test conventions | `SupportIQ.sln` builds the API; the frontend uses npm scripts for build and lint. Feature test projects are not yet established. |
| Backend/frontend | Approved by DEC-041: .NET 10 / ASP.NET Core, React with TypeScript, and Bootstrap. Vite is approved under DEC-043. DEC-044 selects one feature-modular API deployment and a separate frontend application. |
| Database | SQL Server/Azure SQL and EF Core are approved under DEC-041/DEC-050. Schema and environment configuration are not implemented. |
| Identity sessions | No refresh tokens in the first release; reauthentication renews access. User-wide Identity security-stamp validation revokes tokens under DEC-051/DEC-052. Access-token lifetime remains configurable and undecided. |
| Tenant membership | Internal support users have active membership in one tenant only under DEC-053; tenant/role claims are derived from active membership. |
| Sign-in identifier | Email/password sign-in approved under DEC-054; registration, verification, invitation, and password-reset workflows remain deferred. |
| AI | Azure AI Foundry is approved for answer generation and embeddings; exact models, region, deployment, quota, compatibility, and cost envelope remain open. |
| Search, files, background processing | Azure AI Search is approved under DEC-045 for keyword/vector retrieval. Azure Blob Storage is approved under DEC-046 for local and hosted source documents; local development is intended to use an Azure development account under DEC-047, whose availability/configuration is unverified. Asynchronous processing uses an Azure Function triggered by Azure Service Bus under DEC-048; local execution will use a dedicated Azure development namespace under DEC-049, not yet verified. |
| Hosting | Local development/testing followed by a hosted Azure demo is approved; resources and deployment topology are not selected. |
| Reusable capabilities | No application components to reuse were found. Existing planning templates are in `docs/implementation/templates/`. |
| Architecture | DEC-044 approves a modular monolith: one ASP.NET Core API deployment organized into feature-oriented modules and a separate React frontend. Azure AI Search and Azure Blob Storage are selected under DEC-045/DEC-046; document processing uses an Azure Function with Service Bus under DEC-048. EF Core is approved under DEC-050. Local storage/queue account availability and detailed persistence boundaries remain open. |

### Technical approach for planning

The project owner has approved the application stack, Vite frontend tooling, and a modular-monolith backend with a separate React frontend. Continue to resolve detailed API/data/identity contracts and Azure service/configuration choices against approved requirements before dependent feature work or resource provisioning.

## 3. Requirement coverage summary

“Planned” means mapped in this draft; it is not implementation or plan approval. Requirement IDs and their approved status remain as recorded in the PRD and inventory.

| PRD requirement IDs / area | Planned coverage | Coverage status and notes |
|---|---|---|
| BR-001 | FEAT-001, FEAT-003–FEAT-006, FEAT-010–FEAT-012 | Planned; synthetic data and reproducible demo scope included. |
| BR-002; approved first-release `FR-CA-01`–`FR-CA-16`, `FR-KB-01`–`FR-KB-17`, AI-001 | FEAT-002, FEAT-004–FEAT-008 | Planned; covers role-scoped knowledge, the 10 MB per-file upload limit, grounded responses, abstention, citations, and human escalation. |
| BR-003; AI-002; API-001; AC-010, AC-012 | FEAT-002, FEAT-006, FEAT-010, FEAT-012 | Planned; repeatable evidence covers RAG, structured outputs, tenant isolation, and core API invariants; measurable criteria must be decided before release approval. |
| BR-004; AC-013 | FEAT-001, FEAT-009, FEAT-010, FEAT-012 | Planned; numeric service targets remain open and are not invented here. |
| BR-005 | None in first release | Explicitly later-pilot measurement; no KPI, baseline, target, or acceptance criterion is approved. |
| FR-OP-09; AC-006; US-002 | FEAT-003 | Planned; detailed invitation/approval workflow remains a design question. |
| FR-OP-10–FR-OP-14; AC-010 | FEAT-001, FEAT-002, FEAT-012 | Planned; exact token lifetime and refresh-token choice remain open. |
| DATA-002; AC-009 | FEAT-004 | Planned; source and derived content deletion is covered. Backup deletion and log/evaluation-record retention remain open. |
| DATA-003 | FEAT-010 | Planned for fabricated first-release data only; ticket seed strategy remains deferred. |
| ROLE-001–ROLE-005; RULE-009–RULE-024; US-001–US-007; AC-001–AC-008 | FEAT-002–FEAT-009 | Planned; preserve all role, tenant, publication, customer-history, escalation, and Platform Admin boundaries. |
| NFR-007, NFR-011; AC-011 | FEAT-011 | Planned; basic accessibility and English-only first release included; WCAG conformance level remains open. |
| `FR-TK-*`, `FR-AN-*`, ticket/customer-lookup portion of `FR-WF-*`, and other deferred baseline items | None | Intentionally deferred or not promoted by the approved PRD; not silently converted into first-release work. |
| Remaining Draft/unprioritized baseline requirements | None | No disposition inferred. Revisit only through the approved requirements/change process. |

The approved traceability matrix has no test-case IDs. This plan adds work-item IDs and verification activities only; it does not alter the approved requirements traceability artifact.

## 4. Epics

| Epic ID | Name | Outcome | Priority | Feature IDs |
|---|---|---|---|---|
| EPIC-001 | Foundation and tenant security | Approved technical baseline, authenticated identity, tenant isolation, and membership controls. | Must — first-release scope | FEAT-001–FEAT-003 |
| EPIC-002 | Knowledge lifecycle | Validated ingestion, retention, authoring, review, publication, and withdrawal. | Must — first-release scope | FEAT-004–FEAT-005 |
| EPIC-003 | Grounded assistant and human handling | Authorized RAG, isolated conversation history, and agent escalation. | Must — first-release scope | FEAT-006–FEAT-008 |
| EPIC-004 | Platform operations and demonstration | Restricted platform metadata and reproducible local-to-hosted demo operations. | Must — first-release scope | FEAT-009, FEAT-012 |
| EPIC-005 | Quality and inclusive access | Synthetic evaluation, release evidence, English-only UI, and basic accessibility. | Must — first-release readiness | FEAT-010–FEAT-011 |

## 5. Feature catalogue

Estimates are relative T-shirt sizes for feature scope, not durations or commitments. Team capacity and staffing were not supplied.

### FEAT-001 — Approved technical baseline and detailed contracts

- **Epic / estimate / priority:** EPIC-001 / M / Must — prerequisite to implementation.
- **Outcome and value:** Establish only the technical decisions and detailed contracts needed to build the approved slice without treating proposals as approved.
- **In scope:** Confirm backend/frontend choices, architecture boundaries, API/data/auth contracts, and service/configuration choices for local and hosted environments.
- **Out of scope:** Unapproved services, production-scale architecture, ticket/analytics interfaces, and final numeric targets not yet decided.
- **Requirement links:** BR-001, BR-004, API-001, API-002 (decision status only), AI-004, FR-OP-12–FR-OP-14.
- **Acceptance:** Decision record identifies approved choices and unresolved items; API/data/auth contracts preserve the PRD invariants; no proposed default or named Azure service is represented as approved without owner confirmation.
- **Dependencies / risks:** None; resolves blockers before dependent build work. RISK-004, RISK-006.
- **Verification / definition of done:** Project owner reviews required decisions; approved contracts are linked from the plan; unresolved items remain explicit.

### FEAT-002 — Identity, authentication, and tenant authorization

- **Epic / estimate / priority:** EPIC-001 / L / Must.
- **Outcome and value:** Authenticate internal users and external customers and enforce server-derived tenant and role boundaries.
- **Requirement links:** FR-CA-14, FR-OP-10–FR-OP-11, FR-OP-14, API-001, ROLE-001–ROLE-005, RULE-010–RULE-015, AC-001, AC-004, AC-007, AC-010.
- **Acceptance:** JWT carries `UserId`, `UserName`, `Role`, and `exp`; tenant-scoped users also carry `TenantId`, while Platform Admin tokens omit it (DEC-060); tenant and role are validated server-side where applicable; tenant cannot be selected by request parameters/headers; expiry, renewal, and revocation are configurable; unauthorized role/tenant/customer access is denied.
- **Dependencies / risks:** FEAT-001. RISK-001, RISK-007, RISK-008.
- **Verification:** Positive and negative API/integration tests for each approved access boundary; no tenant-content access path bypasses authorization.

### FEAT-003 — Tenant membership management

- **Epic / estimate / priority:** EPIC-001 / M / Must.
- **Outcome and value:** Let Tenant Admins manage tenant membership and internal support-staff provisioning within approved authority.
- **Requirement links:** FR-OP-09, ROLE-001, RULE-013, AC-006, US-002.
- **Acceptance:** Authorized Tenant Admin can invite/provision, update, and immediately deactivate/remove membership; only active tenant membership grants data access; every membership change is audit-logged; higher-level roles act only when explicitly authorized.
- **Dependencies / risks:** FEAT-002. Invitation/approval details remain for design; RISK-001.
- **Verification:** Role-boundary, inactive-membership, membership-audit, and cross-tenant tests.

### FEAT-004 — Knowledge document ingestion and retention

- **Epic / estimate / priority:** EPIC-002 / XL / Must.
- **Outcome and value:** Upload, process, track, update, and remove knowledge documents and derived retrieval data.
- **Requirement links:** Approved first-release `FR-KB-01`–`FR-KB-08`, `FR-KB-17`, DATA-002, AC-009, AC-010, AC-014.
- **Acceptance:** Supported file validation and processing status are visible; files larger than 10 MB are rejected (FR-KB-17 / AC-014); processing failures are not success-shaped; authorized update/reprocess removes stale retrieval content; 90 days after original upload, source, extracted text, chunks, and embeddings are deleted.
- **Dependencies / risks:** FEAT-001, FEAT-002. Search, storage, and worker choices are open. RISK-003, RISK-004.
- **Verification:** Valid/invalid file, processing failure, reprocess, stale-index removal, and retention tests; verify delete coverage for each approved data copy.

### FEAT-005 — Knowledge authoring and external publication governance

- **Epic / estimate / priority:** EPIC-002 / L / Must.
- **Outcome and value:** Support internal knowledge management and controlled external article review/publication.
- **Requirement links:** FR-KB-09–FR-KB-16, ROLE-001–ROLE-003, RULE-009, RULE-016–RULE-024, AC-001, AC-003, AC-008, US-001–US-004.
- **Acceptance:** Tenant Admins and Support Agents can author/edit external articles but cannot approve/reject/publish; authorized Support Managers review, approve, reject, publish, and withdraw; external retrieval is limited to approved and published articles; outdated-content triggers, 90-day default review, overrides, and audit history are honored.
- **Dependencies / risks:** FEAT-002 and FEAT-004's knowledge model. RISK-002, RISK-007.
- **Verification:** Lifecycle transition and permission tests, including attempts to retrieve drafts, rejected, withdrawn, stale, and other-tenant content externally.

### FEAT-006 — Permission-scoped RAG and grounded answers

- **Epic / estimate / priority:** EPIC-003 / XL / Must.
- **Outcome and value:** Deliver relevant knowledge retrieval and grounded answers for internal staff and external customers.
- **Requirement links:** Approved first-release `FR-CA-01`–`FR-CA-13`, AI-001, AI-004, RULE-005, RULE-006, AC-001, AC-002, AC-010.
- **Acceptance:** Retrieval respects active membership, role, permission, and tenant; external requests retrieve only approved/published eligible knowledge; answers cite sources and abstain for missing, conflicting, stale, or insufficient evidence; document content is treated as untrusted input.
- **Dependencies / risks:** FEAT-001, FEAT-002, FEAT-004, FEAT-005. Exact AI deployment and search service are open. RISK-001, RISK-002.
- **Verification:** Retrieval and answer tests for allowed/denied scope, citation/source consistency, abstention, conflicting/stale evidence, prompt-injection cases, and dependency failures.

### FEAT-007 — Isolated assistant conversations and history

- **Epic / estimate / priority:** EPIC-003 / M / Must.
- **Outcome and value:** Provide authenticated assistant conversations and history within each user's authorized scope.
- **Requirement links:** FR-CA-09, FR-CA-14–FR-CA-15, RULE-014–RULE-015, AC-004, US-005.
- **Acceptance:** External customers can access only their own history under their authenticated account and tenant; no customer can access another customer's or internal staff's conversation; retention/deletion behavior is not invented and is decided before implementing that lifecycle.
- **Dependencies / risks:** FEAT-002, FEAT-006. Customer-history retention/deletion is unresolved; RISK-007.
- **Verification:** API and UI tests for owner, tenant, role, and unauthorized-history cases; test approved retention behavior once decided.

### FEAT-008 — Human escalation and agent response

- **Epic / estimate / priority:** EPIC-003 / M / Must.
- **Outcome and value:** Route unanswered customer questions to human support without weakening conversation isolation.
- **Requirement links:** FR-CA-12, FR-CA-16, RULE-001, AC-005, US-006.
- **Acceptance:** A user can escalate an unanswered question; authorized Support Agents can view/respond to that escalated conversation; the customer cannot access other conversation histories.
- **Dependencies / risks:** FEAT-003 and FEAT-007. RISK-007.
- **Verification:** End-to-end escalation, agent response, authorization, and customer-history isolation tests.

### FEAT-009 — Platform operations metadata boundary

- **Epic / estimate / priority:** EPIC-004 / M / Must.
- **Outcome and value:** Support platform operations using only approved platform-level metadata.
- **Requirement links:** ROLE-004, RULE-010–RULE-011, AC-007, US-007.
- **Acceptance:** Platform Admin can inspect permitted platform metadata and aggregated statistics but cannot access tenant-specific business content, customer data, tickets, knowledge articles, or uploaded documents through any operational view or API.
- **Dependencies / risks:** FEAT-001, FEAT-002. RISK-008.
- **Verification:** Positive metadata tests and explicit negative tests against tenant-content identifiers and payloads.

### FEAT-010 — Synthetic assets and AI/RAG evaluation

- **Epic / estimate / priority:** EPIC-005 / L / Must for release readiness.
- **Outcome and value:** Make evaluation repeatable while keeping criteria and data synthetic.
- **Requirement links:** BR-001, BR-003, DATA-003, AI-002, AC-012.
- **Acceptance:** Evaluation assets are versioned and fabricated; owner-approved datasets, measurable metrics, and thresholds cover retrieval, grounding, citations, structured outputs, tenant isolation, core API invariants, abstention, and prompt-injection handling before release approval; runs record model/prompt/deployment identifiers and results; no threshold is invented by this plan.
- **Dependencies / risks:** FEAT-006 and FEAT-001. Evaluation criteria and AI deployment remain open. RISK-002, RISK-004.
- **Verification:** Repeated run produces traceable artifacts and a reviewable results summary; release gate checks the approved criteria.

### FEAT-011 — English-only UI and basic accessibility

- **Epic / estimate / priority:** EPIC-005 / M / Must.
- **Outcome and value:** Provide the approved first-release language and accessibility practices across user-facing workflows.
- **Requirement links:** NFR-007, NFR-011, AC-011.
- **Acceptance:** First-release UI is English-only and supports keyboard navigation, readable contrast, labels, and screen-reader-friendly controls; do not claim a WCAG conformance level until it is approved.
- **Dependencies / risks:** FEAT-001 and user-facing features. WCAG target remains open.
- **Verification:** Keyboard-only and screen-reader checks plus contrast/label review across the implemented flows.

### FEAT-012 — Reproducible local and hosted Azure demonstration

- **Epic / estimate / priority:** EPIC-004 / L / Must for release readiness.
- **Outcome and value:** Enable reproducible setup/testing locally and deployment of the demonstrable release to Azure.
- **Requirement links:** BR-001, BR-004, FR-OP-12–FR-OP-13, AI-004, AC-013.
- **Acceptance:** Setup and deployment instructions are reproducible; Azure SQL is used in both environments; hosted demo configuration contains no committed secrets; monitoring, cost controls, and measurable service targets are documented and tested before release approval.
- **Dependencies / risks:** FEAT-001 and feature integration. Azure resources, models, measurable targets, and cost envelope remain open. RISK-004, RISK-006.
- **Verification:** Clean local setup and test run, hosted smoke/authorization checks, deployment/configuration review, and target-based performance/reliability evidence.

## 6. Delivery sequence and milestones

| Sequence | Work items | Deliverable / exit criteria | Dependencies |
|---|---|---|---|
| M0 — Decision and contract gate | TASK-001–TASK-003 | Project owner confirms the unresolved stack, architecture, service, and API/data/auth decisions needed to proceed. The 10 MB per-file upload limit is confirmed under DEC-040. | None |
| M1 — Secure foundation | FEAT-002–FEAT-003; local setup portion of FEAT-012 | Authentication, tenant/role scope, membership, and negative access tests pass in the selected local setup. | M0 |
| M2 — Knowledge lifecycle | FEAT-004–FEAT-005 | Upload/processing, retention, article authoring/review/publication, and lifecycle tests pass. | M1 |
| M3 — Assistant vertical slice | FEAT-006–FEAT-008 | Internal/external RAG, citations/abstention, isolated conversations, and human escalation work end to end. | M2; model/search decisions |
| M4 — Evaluation and operations | FEAT-009–FEAT-011 | Platform metadata isolation, synthetic evaluation evidence, and basic accessibility checks are complete. | M1–M3 |
| M5 — Hosted demo readiness | Hosted portion of FEAT-012 | Local-to-hosted setup is repeatable; release criteria, operational targets, cost controls, and hosted checks are evidenced. | M0–M4 and owner-approved targets |

### Critical path

Decision/contract approval → identity and tenant authorization → ingestion and article publication → scoped retrieval/RAG → conversation and escalation integration → approved evaluation criteria and hosted release checks.

### Parallelizable work

After FEAT-001 decisions, membership UI/backend work can proceed alongside the ingestion foundation. Accessibility review can run against each UI slice. Synthetic knowledge/evaluation-asset preparation can proceed independently of ticket data, but AI evaluation acceptance criteria depend on the owner-approved metrics and model/search configuration.

### External dependencies

Azure SQL connectivity/configuration; Azure AI Foundry model and embedding availability/quota/compatibility; unresolved search, blob/file, and background-processing service choices; hosted Azure resources; synthetic knowledge and evaluation assets; owner decisions for open questions.

No dates, sprint lengths, or calendar commitments are inferred.

## 7. Non-functional and operational work

- **Security/privacy:** Central tenant/role authorization; enforce server-derived tenant scope; ensure Platform Admin metadata does not expose business content; store secrets outside source; synthetic data only; negative API tests at access boundaries.
- **Reliability:** Surface ingestion/model/search failures; define retry and terminal-failure behavior during detailed design; verify safe failure and recovery without claiming unapproved SLOs.
- **Data lifecycle:** Automate 90-day deletion of source and derived document content; decide backup/log/evaluation and customer-conversation retention before implementing those policies.
- **Accessibility/localization:** English-only UI, keyboard navigation, readable contrast, labels, screen-reader-friendly controls; WCAG level remains open.
- **Performance/cost:** Define approved latency, availability/recovery, concurrency, and cost targets before release approval; test against those targets. No numbers are set in this plan.
- **Observability/platform operations:** Provide permitted health, service, usage, configuration, audit, and aggregate metadata only; verify that no tenant content is exposed.
- **Deployment:** Reproducible local testing followed by hosted Azure demo using Azure SQL in both environments. Do not select unapproved service SKUs or provision resources as part of planning.
- **CI/delivery:** GitHub issue/PR and CI/delivery workflow requirements are deferred; this plan does not silently add a CI platform or workflow feature.

## 8. Estimates and assumptions

- **Method:** Relative T-shirt estimates (`S`, `M`, `L`, `XL`) at feature/task level; not person-days or delivery commitments.
- **Capacity assumptions:** None. Team size, skills, availability, and release date were not supplied.
- **Estimate caveats:** Estimates are provisional because the repository has no application code and key stack, service, API, model, and operating-target decisions remain open. Re-estimate after FEAT-001.
- **Planning assumptions:** Only the approved first-release scope is planned; proposed stack choices remain unapproved; no executable code is assumed to exist. These assumptions do not alter requirements.

## 9. Risks

Likelihood and impact were not rated in the source risk register. They remain unassessed rather than receiving invented scores.

| Risk ID | Description | Likelihood / impact | Mitigation in plan | Owner role | Trigger / contingency |
|---|---|---|---|---|---|
| RISK-001 | Cross-tenant leakage through data, retrieval, filtering, or caching | Unassessed | Centralize scope enforcement and require negative API/integration tests. | Backend developer / security reviewer | Any cross-tenant test or review failure blocks the affected feature. |
| RISK-002 | Inaccurate or overconfident AI output | Unassessed | Require citations, abstention, human escalation, synthetic evaluation cases, and owner-approved thresholds. | AI/application developer / project owner | Evaluation fails an approved threshold or evidence is unsupported. |
| RISK-003 | Document parsing/indexing failures | Unassessed | Expose processing states/errors; verify invalid, partial, retry, reprocess, and stale-index behavior. | Application developer | Processing is shown as successful without usable indexed content. |
| RISK-004 | Cloud/AI costs exceed the learning budget | Unassessed | Resolve deployment/cost choices, track usage where available, and define a release cost target before hosted approval. | Project owner / cloud implementer | Quota, pricing, or target cannot support the demonstrator. |
| RISK-005 | First-release scope exceeds available delivery capacity | Unassessed | Preserve the approved knowledge/RAG vertical slice and exclusions; do not infer a 30-day deadline or team capacity. | Project owner | Any proposed work expands into deferred capabilities or an unapproved schedule commitment. |
| RISK-006 | Local and hosted environment expectations diverge | Unassessed | Confirm the environment/service design and verify both setup paths. | Cloud implementer | Hosted demo cannot reproduce local behavior or approved security constraints. |
| RISK-007 | Internal/external access or escalation exposes conversations/knowledge | Unassessed | Isolate customer history and test each role/publication boundary end to end. | Application developer / security reviewer | An unauthorized conversation or article is visible. |
| RISK-008 | Platform diagnostics expose tenant content | Unassessed | Allowlist metadata and add negative content-leak tests for operational views/APIs. | Platform implementer / security reviewer | Operational response contains tenant-specific business content. |

## 10. Assumptions and open questions

| ID | Type | Description | Planning impact | Owner / status |
|---|---|---|---|---|
| Q-007 | Open question | Exact AI models, region, deployment, quota/compatibility, and AI cost envelope. | Resolve before finalizing integration and cost estimates. | Project owner / partially answered |
| Q-012 | Open question | Numeric latency, availability/recovery, concurrency, and operating-cost targets. | Required for performance and release-readiness evidence; no values assumed. | Project owner / open for detailed targets |
| Q-011 | Open question | Evaluation datasets, metrics, and acceptance thresholds. | Define and approve before release approval; do not invent rubric/thresholds. | Project owner / open for detailed criteria |
| Q-014 | Open question | WCAG conformance level. | Apply approved basic practices; do not claim a conformance level. | Project owner / open |
| Q-010 | Open question | Backup deletion and log/evaluation-record retention. | Implement approved source/derived deletion; resolve other retention policies before setting those lifecycles. | Project owner / partially answered |
| Q-025 | Open question | External-customer conversation-history retention/deletion. | Owner decision required before implementing conversation-history lifecycle policy. | Project owner / partially answered |
| Q-019 / API-001 | Open design item | Detailed API paths, schemas, validation, pagination, idempotency, and error formats. | Define contracts in FEAT-001 without changing approved auth, tenant, role, knowledge-access, and deletion invariants. | Project owner / deferred to design |
| Q-006 / Q-008 | Open design items | Exact token lifetime/refresh-token choice and detailed invitation/approval or role-restriction assignment workflows. | Design configurable auth and preserve approved role authority; obtain decisions before affected behavior is fixed. | Project owner / deferred to design |
| API-002 / technology baseline | Open design items | Search, Blob Storage, background-processing service, and resource configuration. | Do not select or provision services until the project owner approves the design. | Project owner / open |
| DEC-041 / DEC-043 | Approved technology/tooling | .NET 10 / ASP.NET Core, React with TypeScript, Bootstrap, SQL Server, local database identity with JWT, Azure AI Foundry, and Vite frontend tooling are approved. | Implement the approved baseline; detailed architecture boundaries and service/configuration decisions remain open under TASK-001–TASK-003. | Project owner / approved |
| DEC-033 | Deferred scope | GitHub issue/PR, CI, and delivery workflow requirements. | Excluded from this first-release plan unless scope is separately approved. | Project owner / deferred |

## 11. Dependency graph and sequencing

```text
FEAT-001 decisions/contracts
  └─ FEAT-002 identity and tenant authorization
       ├─ FEAT-003 membership
       ├─ FEAT-004 ingestion and retention
       │    └─ FEAT-005 article governance
       │         └─ FEAT-006 scoped RAG
       │              └─ FEAT-007 conversations/history
       │                   └─ FEAT-008 escalation
       └─ FEAT-009 platform operations metadata
FEAT-006 ── FEAT-010 AI/RAG evaluation ──┐
FEAT-001 ── FEAT-011 accessibility       ├─ FEAT-012 hosted release readiness
FEAT-002..FEAT-009 ──────────────────────┘
```

Dependencies in the task board are one-way and do not form cycles. Features may be resequenced after technical decisions, but requirement scope and release gates must remain unchanged.

## 12. Approval history

| Version | Date | Decision | Approver | Notes |
|---|---|---|---|---|
| 0.1 | 2026-11-12 | Draft prepared under Gate 5 authorization | Project owner | DEC-038 / EV-064. |
| 0.1 | 2026-11-12 | Plan approved as written | Project owner | DEC-039 / EV-065. Implementation authorization was pending at plan approval. |
| 0.2 | 2026-11-12 | Updated approved plan to reflect the confirmed 10 MB per-file limit | Project owner decision recorded as DEC-040 / EV-066 | Requirement/task alignment only; implementation authorization was pending. |
| 0.3 | 2026-11-12 | Recorded implementation authorization, approved stack/tooling, and the initial scaffold task | Project owner | DEC-041–DEC-043 / EV-067–EV-069. No product requirements or Azure resource decisions are changed. |
| 0.4 | 2026-11-12 | Recorded modular-monolith architecture decision | Project owner | DEC-044 / EV-070; detailed contracts and service decisions remain open. |
| 0.5 | 2026-11-12 | Recorded Azure AI Search selection for knowledge retrieval | Project owner | DEC-045 / EV-071; resource and index configuration remain open. |
| 0.6 | 2026-11-12 | Recorded Azure Blob Storage selection for local and hosted source documents | Project owner | DEC-046 / EV-072; local connection method and resource configuration remain open. |
| 0.7 | 2026-11-12 | Recorded Azure development storage account as the intended local Blob connection | Project owner | DEC-047 / EV-073; account availability/configuration unverified; no resource access/provisioning authorized. |
| 0.8 | 2026-11-12 | Recorded Azure Function with Service Bus queue trigger for document processing | Project owner | DEC-048 / EV-074; queue configuration, local connection, and resource decisions remain open. |
| 0.9 | 2026-11-12 | Recorded dedicated Azure development Service Bus namespace for local Function execution | Project owner | DEC-049 / EV-075; namespace availability/configuration unverified; no resource access/provisioning authorized. |
| 1.0 | 2026-11-12 | Recorded EF Core as the SQL Server/Azure SQL persistence technology | Project owner | DEC-050 / EV-076; schema and connection configuration remain open. |
| 1.1 | 2026-11-12 | Recorded first-release no-refresh-token behavior and user-wide security-stamp revocation | Project owner | DEC-051–DEC-052 / EV-077–EV-078; access-token lifetime remains open. |
| 1.2 | 2026-11-12 | Recorded single-tenant membership for internal support users | Project owner | DEC-053 / EV-079; detailed membership workflow remains open. |
| 1.3 | 2026-11-12 | Recorded email/password as the sign-in identifier | Project owner | DEC-054 / EV-080; account lifecycle workflows remain deferred. |
| 1.4 | 2026-11-12 | Amended the Platform Admin JWT tenant-claim requirement | Project owner explicitly approved the requirement change | DEC-060 / EV-086 / CHG-004; tenant-scoped tokens retain `TenantId`; Platform Admin tokens omit it. |

## 13. Implementation authorization boundary

Implementation is authorized under DEC-042. This does not resolve open requirements/design decisions or authorize Azure resource provisioning. Continue to gate dependent implementation on the decisions identified in this plan and task board.
