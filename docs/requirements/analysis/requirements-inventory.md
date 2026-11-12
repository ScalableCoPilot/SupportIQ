# SupportIQ Requirements Inventory

## Status and classification

This inventory records the Gate 3-approved requirements package and preserves the status of each item. The owner approved stakeholder-confirmed first-release requirements and the candidate stories/acceptance criteria as presented. Baseline-only statements explicitly left Draft or unprioritized remain unapproved and are not assumed in or out of scope. “Source-supported” means wording appears in the source; it does not by itself mean stakeholder-approved.

Source: [SupportIQ-Baseline.md](../baseline/SupportIQ-Baseline.md). Requirement IDs already present in the baseline are retained unchanged. IDs assigned during analysis were not approved merely by being assigned; the status column records the applicable Gate 3 disposition.

## Business requirements

| ID | Initial requirement statement | Source classification | Status | Trace |
|---|---|---|---|---|
| BR-001 | Demonstrate a customer-support knowledge portal as a learning/portfolio project using synthetic data and production-minded engineering practices. | Source-supported | Approved at Gate 3 | Executive Summary; Confirmed Baseline Decisions |
| BR-002 | Help support agents locate approved information and prepare grounded responses, while retaining human responsibility for customer-facing decisions. | Source-supported | Approved at Gate 3 | Executive Summary; AI guardrails |
| BR-003 | Demonstrate repeatable quality evaluation for retrieval, grounding, citations, structured outputs, tenant isolation, and core APIs. | Source-supported | Approved at Gate 3; measurable criteria due before release approval | Goals and Success Measures; Test Strategy |
| BR-004 | Make setup, testing, monitoring, cost controls, and deployment reproducible for a demonstrable application. | Source-supported | Approved at Gate 3; numeric operating targets remain deferred | Goals and Success Measures; Definition of Done |
| BR-005 | Measure any reduction in search and routine reply-composition effort in a later pilot rather than claim an unverified benefit. | Source-supported | Approved at Gate 3 for a later pilot; no KPI or target approved | Goals and Success Measures |

The baseline does not provide an approved business KPI, baseline measurement, or target for the later pilot.

## Functional requirements

### Customer assistant — source IDs `FR-CA-01`–`FR-CA-16`

Conversation and natural-language questions; authorization-filtered retrieval; grounded answers with source references; clear abstention and possible escalation; tenant/access-safe conversational context; feedback; permission-controlled history. English-only support is confirmed for the first release; additional language support is not confirmed.

The owner approved the first-release Knowledge Management with RAG slice at Gate 3, including the baseline-derived assistant and knowledge-ingestion capabilities that implement that slice. Other baseline capabilities remain Draft unless separately approved or explicitly deferred.

Stakeholder discovery confirmed that both internal support staff and external customers are intended assistant audiences in the first release. These requirements were approved at Gate 3:

| ID | Initial requirement statement | Source classification | Status | Trace |
|---|---|---|---|---|
| FR-CA-09 | The first-release assistant is intended for use by both internal support staff and external customers. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-002 |
| FR-CA-10 | External-customer assistant retrieval is limited to publicly approved knowledge. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-016 |
| FR-CA-11 | External customers can access only knowledge that is both approved and published. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-009 |
| FR-CA-12 | Users can escalate unanswered assistant questions to human support. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-003 |
| FR-CA-13 | Assistant retrieval and answers must follow the access permissions applicable to internal staff and external customers. Support Agents may retrieve internal knowledge in all lifecycle statuses and, by default, published external knowledge within their own tenant unless role- or permission-based restrictions are configured; Support Managers may manage those restrictions and retrieve all knowledge statuses in their tenant. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview records](../evidence/interview-records.md), Gate 2, Q-003, Q-008, Q-021, and Q-022; baseline `FR-CA-02` |
| FR-CA-14 | External customers authenticate using Identity backed by Azure SQL with JWT-based authentication. Each customer account is associated with a tenant during registration or invitation; the application derives tenant scope from the authenticated user's server-side identity and prohibits tenant selection or changes through request parameters or headers. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-005 and Q-024 |
| FR-CA-15 | External customers may access only conversation history created under their authenticated account and associated tenant; they must never access another customer's or internal staff's conversations. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-025 |
| FR-CA-16 | Support Agents may view and respond to external customer conversations escalated to human support. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-008 |

The project owner stated that a Support Manager or explicitly authorized higher-level role is responsible for external-use approval. Support Agent access to published external knowledge defaults to all such knowledge within the agent's own tenant unless a Support Manager configures role- or permission-based restrictions. Detailed assignment rules may be finalized during detailed design. External customer tenant association is derived server-side from authenticated identity, and customers can access only their own conversations under that account and tenant. Registration/verification workflows and conversation history retention/deletion policies remain unresolved and are deferred to design.

### Knowledge management — source IDs `FR-KB-01`–`FR-KB-17`

Authorized PDF/DOCX/TXT upload; validation of extension, content type, size, and processing outcome; source/version/tenant/uploader/status metadata; extraction, normalization, configurable chunking, embedding, indexing; visible lifecycle status; authorized update/reprocess; removal of stale index content; deletion of source and derived content from availability; source identification in search/citations.

The baseline states a 10 MB per-file maximum in its confirmed-decisions table and risks section. The project owner subsequently confirmed that the 10 MB limit applies to the first release, resolving Q-033 under DEC-040. The baseline also specifies 90-day document retention; stakeholder follow-up set the retention start to original upload and confirmed deletion of source documents, extracted text, chunks, and embeddings after expiry. Backup deletion and log/evaluation-record retention remain open.

| ID | Initial requirement statement | Source classification | Status | Trace |
|---|---|---|---|---|
| FR-KB-09 | Support Agents upload and manage knowledge documents; Support Managers review, approve, reject, and publish knowledge for external use, and only articles explicitly approved and published by the Support Manager or an authorized role are externally accessible. Articles must be accurate, up to date, customer-friendly, free from confidential, sensitive, or internal-only information, and must not expose another tenant's data. Higher-level roles may perform these actions only when explicitly authorized. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview records](../evidence/interview-records.md), Gate 2, Q-003, Q-009, Q-028, and Q-029 |
| FR-KB-10 | When an external article is identified as outdated, flag it for review and temporarily withdraw it from external access until updated and reapproved by the Support Manager or an explicitly authorized role. Audit all changes. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-030 |
| FR-KB-11 | Flag an article for review when its review date expires, content becomes inaccurate, a related product or process changes, or a user reports an issue. Support Managers may also flag articles manually. Review frequency must be configurable. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-031 |
| FR-KB-12 | Published external knowledge has a default review interval of 90 days. Support Managers may configure a different review date for an individual article. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-032 |
| FR-KB-13 | Tenant Admins may read and manage knowledge content in all lifecycle statuses within their own tenant, including draft, pending review, approved, rejected, and published. They may create/edit external articles for Support Manager review but may not approve, reject, or publish them. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview records](../evidence/interview-records.md), Gate 2, Q-008 |
| FR-KB-14 | Support Agents may create, read, and manage internal knowledge across their own tenant, independent of who uploaded it. They may retrieve internal knowledge in all lifecycle statuses. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview records](../evidence/interview-records.md), Gate 2, Q-008 and Q-021 |
| FR-KB-15 | Support Agents may create and edit external knowledge articles for Support Manager review. They may not approve, reject, or publish external articles. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-008 |
| FR-KB-16 | Tenant Admins may create and edit external knowledge articles for Support Manager review. They may not approve, reject, or publish external articles. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-008 |
| FR-KB-17 | Each uploaded file must be no larger than 10 MB. | Confirmed by stakeholder response | Approved by project owner on 2026-11-12 under DEC-040 | [Interview record](../evidence/interview-records.md), Q-033; EV-066 |

The stakeholder-confirmed 90-day knowledge review interval is separate from the 90-day document-retention period. Backup deletion and log/evaluation-record retention remain open for detailed design and compliance review.

### Ticket intelligence — source IDs `FR-TK-01`–`FR-TK-07`

Synthetic ticket list/detail; concise summaries; configurable category/priority classification with structured output; provisional sentiment/urgency; supported queue/escalation recommendations; human override with appropriate preservation of suggestion and final value; safe handling of invalid model output.

### Agent copilot — source IDs `FR-AC-01`–`FR-AC-07`

Ticket-specific reply drafts; sourced knowledge recommendations; authorized customer-context summary; knowledge-supported next steps; edit/copy/discard/regenerate controls; no automatic sending in release one; distinguish internal notes from customer-facing drafts.

### Workflow automation and tools — source IDs `FR-WF-01`–`FR-WF-06`

Small allowlisted tool set for knowledge search and read-only ticket/customer lookup; typed contracts and server-side authorization; bounded timeout/error handling; no arbitrary SQL, shell, or unrestricted network execution; human confirmation for business-data changes; audit actor, tenant, outcome, and correlation data; safe tool failures.

### Support analytics — source IDs `FR-AN-01`–`FR-AN-05`

Authorized ticket counts by status/category/priority; conditional trends/SLA indicators; limited natural-language questions through predefined analytics functions; visible data scope/time range; arbitrary text-to-SQL excluded.

### AI evaluation/testing — source IDs `FR-EV-01`–`FR-EV-06`

Versioned evaluation set; record retrieval/answer/citations/latency/model/prompt metadata; assess relevance, grounding, citation correctness, and abstention; compare changes against baseline; include ambiguity, missing/conflicting knowledge, prompt injection, and cross-tenant cases; document thresholds and limitations without treating evaluation as proof.

Baseline proposes initial asset volumes: 20 knowledge articles/FAQs, 100 synthetic tickets, 5 fictional organizations, 10 support agents, 50 question/source pairs, 10 no-answer questions, and 10 prompt-injection cases. These are proposed volumes pending validation, not approved quality thresholds. The owner deferred synthetic ticket taxonomy, fields, and seed strategy until ticket AI and analytics are included in a future phase.

### Security and AI operations — source IDs `FR-OP-01`–`FR-OP-14`

Tenant association and scope on data paths; role access on APIs and relevant UI actions; managed secret storage; useful error/latency/model-use/correlation telemetry; minimize sensitive log content and configure retention/redaction; request/rate limits, timeouts, graceful model/search failure; approximate AI usage/cost tracking where available; repeatable CI/CD deployment/configuration.

| ID | Initial requirement statement | Source classification | Status | Trace |
|---|---|---|---|---|
| FR-OP-09 | Tenant Admin manages tenant users and membership, including inviting/provisioning internal support staff accounts, assigning users to the appropriate tenant, updating membership and role permissions, and immediately removing or deactivating membership when access is no longer required. Higher-level roles may do so only when explicitly authorized. Users may access only data belonging to their active tenant membership, and all membership changes must be recorded in audit logs. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview records](../evidence/interview-records.md), Gate 2, Q-006, Q-023, and Q-028 |
| FR-OP-10 | JWT access-token expiry must be configurable; the exact token lifetime will be finalized during detailed design based on security requirements and user experience. | Confirmed by stakeholder response | Approved at Gate 3; lifetime deferred | [Interview record](../evidence/interview-records.md), Gate 2, Q-026 |
| FR-OP-11 | Authentication design must support configurable token renewal and revocation; whether to use refresh tokens will be decided during detailed design based on security, session management, and user experience. | Confirmed by stakeholder response | Approved at Gate 3; refresh-token choice deferred | [Interview record](../evidence/interview-records.md), Gate 2, Q-027 |
| FR-OP-12 | Develop and test the initial build locally, then deploy the demonstrable release as a hosted Azure demo. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-004 |
| FR-OP-13 | Use Azure SQL for the local-development and hosted environments. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview record](../evidence/interview-records.md), Gate 2, Q-005 |
| FR-OP-14 | JWTs include UserId, UserName, TenantId, Role, and expiration (`exp`) claims. Validate TenantId and Role server-side for authorization. Additional permissions or claims may be finalized during detailed design. | Confirmed by stakeholder response | Approved at Gate 3 | [Interview records](../evidence/interview-records.md), Gate 2, Q-006 |

Invitation and approval workflow details may be finalized during design.

## Non-functional requirements

The baseline has no NFR identifiers. The following provisional IDs are assigned for analysis traceability only.

| ID | Quality area | Initial source-supported statement | Status |
|---|---|---|---|
| NFR-001 | Security | HTTPS, protected secrets, validated input, server-side tenant/role authorization, and least privilege. | Draft |
| NFR-002 | Privacy | Synthetic data; minimize logged content; document retention/deletion. | Draft |
| NFR-003 | Reliability | Handle timeouts, throttling, transient errors, partial ingestion failures, and safe retries. | Draft |
| NFR-004 | Performance | Paginate and ingest asynchronously; establish latency baselines before making guarantees. | Draft |
| NFR-005 | Scalability | Asynchronous ingestion, loosely coupled services, and no reliance on in-memory state. | Draft |
| NFR-006 | Maintainability | Layered boundaries, dependency injection, typed contracts, structured logging, and documented configuration. | Draft |
| NFR-007 | Accessibility | Follow basic accessibility practices including keyboard navigation, readable contrast, labels, and screen-reader-friendly controls. The baseline also recommends clear loading/error states. | Approved at Gate 3; WCAG conformance level remains open |
| NFR-008 | Observability | Correlate UI/API/worker/model/search activity; record latency and failure rates without excess personal data. | Draft |
| NFR-009 | Cost | Budgets/alerts where available; cap model input/output; document usage and teardown. | Draft |
| NFR-010 | Portability | Keep provider-specific code behind interfaces where practical and document cloud dependencies. | Draft |
| NFR-011 | Localization | Support English only in the first release. | Approved at Gate 3 |

No numeric performance, availability, recovery, cost ceiling, accessibility conformance level, or log-retention target is stated.

The project owner confirmed that no numeric latency, availability/recovery, concurrency, or operating-cost targets are set yet. Measurable targets must be defined during detailed design and performance testing before release approval.
The project owner confirmed English-only first-release support and basic accessibility practices; the WCAG conformance level remains open for detailed design.

## Roles

| ID | Role | Responsibility/access summary | Status |
|---|---|---|---|
| ROLE-001 | Tenant Admin | Manage tenant organization settings, tenant users and membership (including internal support staff invitations/provisioning), knowledge sources, and all-status knowledge content within their own tenant; create/edit external articles for Support Manager review but not approve, reject, or publish. | First-release knowledge/membership boundaries approved at Gate 3; detailed invitation/approval workflow deferred; non-knowledge permissions for out-of-scope capabilities deferred |
| ROLE-002 | Support Agent | Create, read, and manage all internal knowledge within their own tenant, regardless of uploader; retrieve internal knowledge in all lifecycle statuses; create/edit external articles for Support Manager review but not approve, reject, or publish them; by default retrieve published external knowledge within the tenant unless role- or permission-based restrictions are configured; view/respond to escalated external customer conversations. | First-release knowledge, retrieval, and escalation boundaries approved at Gate 3; detailed restriction assignment deferred; non-knowledge permissions for out-of-scope capabilities deferred |
| ROLE-003 | Support Manager | Manage support operations and knowledge article review, approval, rejection, and publication; retrieve all knowledge within the manager's tenant, including draft, pending-review, approved, rejected, and published articles; manage role/permission restrictions. | First-release knowledge lifecycle responsibilities approved at Gate 3; non-knowledge permissions for out-of-scope capabilities deferred |
| ROLE-004 | Platform Admin | Operate the platform and investigate issues using only platform-level operational metadata; no access to tenant business content. | Boundary and metadata scope approved at Gate 3 |
| ROLE-005 | External Customer | Intended assistant audience; authenticates with Identity backed by Azure SQL and JWT; account is explicitly associated with a tenant and tenant scope is derived server-side from authenticated identity. | Audience and tenant-binding boundary approved at Gate 3; registration/verification workflow and conversation-history retention/deletion deferred |

The baseline does not list an External Customer role or define detailed permission matrices, external-customer identity, user membership across tenants, tenant provisioning, or administration of multiple tenants.

## Business rules and AI guardrails

The baseline and stakeholder discovery support the following provisional rules:

- RULE-001: Retrieval and conversation history must honor the user’s role, tenant, and access boundaries.
- RULE-002: Customer-facing drafts require human review; no automatic sending in the first release.
- RULE-003: Business-data changes require explicit human confirmation; write actions may be deferred.
- RULE-004: Model tools are allowlisted, typed, authorized, bounded, and audited; arbitrary SQL, shell commands, and unrestricted network requests are not allowed.
- RULE-005: Generated support answers must be grounded in approved retrieved knowledge, cite sources, and abstain when evidence is missing, conflicting, stale, or insufficient.
- RULE-006: Documents, tickets, and retrieved passages are untrusted data and must not be treated as model instructions.
- RULE-007: Structured model output must be validated before persistence or downstream use; AI classifications and sentiment remain provisional and editable.
- RULE-008: Use fabricated demo content only; do not place real customer data or secrets in prompts, logs, fixtures, or screenshots.
- RULE-009: External-customer knowledge approval is handled by a Support Manager or explicitly authorized higher-level role; only approved and published knowledge is available to external customers.
- RULE-010: Platform Admin must not access tenant business content; the owner confirmed this is a categorical prohibition. Platform Admin access is limited to approved platform metadata and operational information.
- RULE-011: Platform Admin may access only platform-level operational metadata, including system health, application logs, service status, usage metrics, configuration, audit logs, and aggregated platform statistics. This access must not expose tenant-specific business content, customer data, tickets, knowledge articles, or uploaded documents.
- RULE-012: Support Agents may retrieve internal knowledge in all lifecycle statuses and, by default, published external knowledge within their own tenant unless role- or permission-based restrictions are configured. Support Managers may manage those restrictions and retrieve all knowledge statuses within their own tenant. Tenant isolation must always be enforced, and Platform Admins must not access tenant knowledge.
- RULE-013: Tenant Admin manages tenant users and membership by inviting/assigning, updating, and immediately removing/deactivating access when no longer required. Higher-level roles may perform these actions only when explicitly authorized. Users may access only data belonging to their active tenant membership, and all membership changes must be recorded in audit logs. Detailed invitation and approval workflows may be finalized during design.
- RULE-014: External customer accounts are associated with a tenant during registration or invitation. The application derives tenant scope from the authenticated user's server-side identity; users must not select or change tenant scope through request parameters or headers.
- RULE-015: External customers may access only conversation history created under their authenticated account and associated tenant. They must not access another customer's conversations or internal staff conversations. Conversation-history retention and deletion policies may be finalized during detailed design.
- RULE-016: Tenant Admin manages tenant users, membership, and knowledge sources. Support Manager manages support operations and knowledge article review, approval, rejection, and publication. Higher-level roles may perform these actions only when explicitly authorized.
- RULE-017: Articles for external access must be accurate, up to date, customer-friendly, and free from confidential, sensitive, or internal-only information; they must not expose another tenant's data. Only explicitly approved and published articles are externally accessible.
- RULE-018: Outdated external articles must be flagged for review and temporarily withdrawn from external access until updated and reapproved by a Support Manager or explicitly authorized role. All changes must be audit-logged.
- RULE-019: Flag external articles for review when review date expires, content becomes inaccurate, a related product/process changes, or a user reports an issue; Support Managers may manually flag articles. Review frequency must be configurable.
- RULE-020: Published external knowledge has a default 90-day review interval; Support Managers may set a different review date for an individual article. This does not change the baseline's separate 90-day document-retention statement.
- RULE-021: Tenant Admins may read and manage knowledge content in all lifecycle statuses within their own tenant and may create/edit external articles for Support Manager review. They may not approve, reject, or publish external articles.
- RULE-022: Support Agents may create, read, and manage internal knowledge throughout their own tenant, independent of uploader; retrieval includes all lifecycle statuses.
- RULE-023: Support Agents may create and edit external knowledge articles for Support Manager review, but may not approve, reject, or publish them.
- RULE-024: Tenant Admins may create and edit external knowledge articles for Support Manager review, but may not approve, reject, or publish them.

RULE-001 through RULE-008 remain Draft baseline statements. RULE-009 through RULE-024 are approved at Gate 3; deferred implementation/design details remain listed with the associated requirements.

## Data, integration, and AI requirements

| ID | Area | Initial extraction | Source | Status |
|---|---|---|---|---|
| DATA-001 | Data | Illustrative entities include tenants, users/memberships, knowledge documents/chunks, conversations/messages, citations, tickets, ticket AI results, feedback, tool audit, and evaluation runs. | Core Data Entities | Draft; schema is illustrative |
| DATA-002 | Lifecycle | Record document tenant/uploader/timestamp/version/status; the 90-day retention period starts on original upload, after which the source document, extracted text, chunks, and embeddings are deleted. | `FR-KB-03`–`FR-KB-07`; Confirmed Baseline Decisions; stakeholder response Q-010 | Approved at Gate 3; backup/log/evaluation-record retention remains deferred |
| DATA-003 | Synthetic data | Use fabricated organizations, agents, tickets, knowledge, and evaluation assets only. | Sample Data and Evaluation Assets | Approved at Gate 3; ticket taxonomy, fields, and seed strategy deferred |
| API-001 | API | Example contracts cover chat/history, knowledge upload/status/reindex/delete, tickets, ticket AI, reply drafts, feedback, and health. Detailed schemas, endpoint paths, validation, pagination, idempotency, and error formats are deferred to solution/detailed design. Requirements must confirm authentication, tenant isolation, role-based authorization, secure knowledge access, and consistent deletion across source and derived data. | API and Integration Requirements; stakeholder response Q-019 | Requirements-level invariants approved at Gate 3; detailed contracts deferred |
| API-002 | External services | Baseline names Azure AI model endpoint, Azure AI Search, Blob Storage, Azure SQL, and background worker/Azure Functions; production ticketing/CRM/email/messaging integrations are deferred. | Technology baseline; High-Level Architecture; Scope | Draft; Azure SQL and Azure AI Foundry decisions are recorded separately |
| AI-001 | RAG | Retrieve only authorized knowledge; show source references; abstain where evidence is inadequate or conflicting; keep tenant boundaries. | `FR-CA-*`; AI-Specific Guardrails | Approved at Gate 3 for the confirmed first-release RAG slice |
| AI-002 | Evaluation | Version data/prompts and capture model/deployment/run details; evaluate retrieval, groundedness, citations, abstention, structured outputs, and prompt injection. Define measurable metrics, evaluation datasets, and acceptance thresholds during AI/RAG detailed design before release approval. | `FR-EV-*`; Test Strategy; stakeholder response Q-011 | Approved at Gate 3 as a design/release-readiness requirement; exact metrics and thresholds deferred |
| AI-003 | Human oversight | Human agents review/edit/discard drafts and own customer-facing actions; suggestions are not verified facts. | `FR-AC-*`; Executive Summary; AI-Specific Guardrails | Draft; associated agent-copilot scope is not confirmed for first release |
| AI-004 | Model provider | Use Azure AI Foundry for answer generation and embeddings. Exact models, region, and cost envelope are deferred to detailed design; deployment configuration remains open. | Confirmed by stakeholder response; [interview records](../evidence/interview-records.md), Gate 2, Q-007 | Azure AI Foundry provider approved at Gate 3; deployment details deferred |

The entities are illustrative, not a finalized schema. Data ownership, data classification, retention schedules beyond documents, migration, backup deletion, and field-level sensitivity remain unspecified.

## Stakeholder-confirmed first-release vertical slice

The project owner identified end-to-end Knowledge Management with a RAG-based AI Assistant as the must-have first demonstrable release and approved the requirements package at Gate 3. The expected workflow is:

1. A Support Agent uploads and manages knowledge documents.
2. A Support Manager or explicitly authorized higher-level role reviews and approves knowledge for external use.
3. The assistant retrieves relevant approved knowledge and generates grounded answers.
4. Internal staff and external customers receive answers according to their access permissions; external customers can access only approved and published knowledge.
5. Users can escalate unanswered questions to human support.

This first-release priority is Approved at Gate 3. Deferred and unresolved design details retain their recorded statuses.

| Confirmed later-phase deferral | Baseline capability mapping | Status / boundary |
|---|---|---|
| Ticket list/detail | `FR-TK-01` | Deferred from release one |
| Ticket summary/classification and advanced ticket intelligence | `FR-TK-02`–`FR-TK-07` | Deferred from release one |
| Simple dashboard and analytics | `FR-AN-01`–`FR-AN-05` | Deferred from release one |
| Read-only ticket/customer lookup tools | Lookup portion of `FR-WF-01` | Deferred from release one; knowledge search/retrieval remains required for RAG |
| Additional AI tools | Additional tool capabilities in `FR-WF-*` | Later phase; core RAG retrieval is not deferred |

These scope decisions were approved as part of the Gate 3 requirements package. Internal staff knowledge scopes include default access to published external knowledge within each Support Agent's own tenant and Support Manager management of role/permission restrictions. Detailed restriction assignment rules may be finalized during detailed design; tenant membership lifecycle and other permission details remain open.

## Acceptance criteria and traceability outline

The source’s acceptance criteria cover:

- Authorized document upload through success/failure status and eventual retrieval/citation.
- Clear abstention when no support exists.
- Denial of cross-tenant access through direct APIs.
- Schema-conforming ticket AI output, with invalid output rejected or safely retried.
- Editable/discardable drafts and no automatic send.
- Authorized, bounded, audited tools.
- Build and automated tests in pull-request CI with failures blocking the normal merge path (baseline acceptance guidance; workflow requirements deferred to the next phase under Q-018).
- Documented setup/deployment with no repository secrets.
- Repeatable evaluation runs recording model/prompt identifiers.

Gate 3-approved traceability is summarized below; user stories and acceptance criteria are listed in [requirements-traceability.md](requirements-traceability.md). Test-case IDs and executable test designs are not assigned.

| Business requirement | Related source requirements/capabilities | Source acceptance coverage |
|---|---|---|
| BR-001 | Tenant-aware platform and synthetic-only data; synthetic ticket taxonomy/fields/seed deferred | Synthetic-only in-scope data; reproducible setup remains a candidate |
| BR-002 | First-release `FR-CA-*`, `FR-KB-*`, `AI-001`, and `AI-003`; ticket/agent-copilot features deferred where outside the confirmed vertical slice | Upload/retrieve/cite, permission boundaries, abstention, and human escalation |
| BR-003 | `FR-EV-*`, `FR-OP-*`, `NFR-001` | Evaluation run and tenant-isolation evidence; measurable AI/RAG thresholds deferred to detailed design before release approval |
| BR-004 | `FR-OP-04`–`FR-OP-08`, `NFR-003`–`NFR-010` | Setup, deployment, and telemetry; CI/delivery workflow scope deferred to the next phase |
| BR-005 | Later pilot measurement; no baseline measurement requirement yet | No measurable acceptance criterion defined |

The project owner approved the requirements package and its stories, acceptance criteria, traceability, and stated priorities at Gate 3. The resulting PRD was approved at Gate 4 with Q-033 open; the owner subsequently confirmed the 10 MB per-file maximum under DEC-040. Explicitly Draft/unprioritized baseline items and other unresolved/deferred decisions retain their recorded statuses.
