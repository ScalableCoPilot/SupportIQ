# SupportIQ Product Requirements Document

## 1. Document information

| Field | Value |
|---|---|
| Document status | Approved at Gate 4 |
| Requirements gate | Gate 3 package approved as presented |
| PRD approval | Approved by project owner; date not recorded |
| Post-approval changes | CHG-001 / DEC-040 confirms the 10 MB per-file upload maximum; CHG-002 records approved implementation technology and design decisions; CHG-003 / DEC-055 defines the limit as 10,000,000 bytes; CHG-004 / DEC-060 amends the Platform Admin TenantId claim requirement |
| Implementation planning | Gate 5 authorized; plan approved; implementation authorized under DEC-042 |
| Source of truth | [Gate 3 requirements inventory](../analysis/requirements-inventory.md), [traceability matrix](../analysis/requirements-traceability.md), and linked evidence |
| Original baseline | [SupportIQ-Baseline.md](../baseline/SupportIQ-Baseline.md); preserved unchanged |

This PRD consolidates the Gate 3-approved requirements and was approved at Gate 4 with Q-033 open. The project owner subsequently confirmed the 10 MB per-file upload maximum under DEC-040, specified its exact byte threshold under DEC-055, made the implementation technology/design decisions listed in CHG-002, and amended the Platform Admin JWT tenant-claim requirement under DEC-060. Explicitly Draft/unprioritized baseline items and other unresolved or deferred decisions retain their existing status and are not promoted by this document.

## 2. Executive summary

SupportIQ is an AI-powered customer-support knowledge portal intended to help support teams manage approved knowledge and retrieve grounded answers. The first demonstrable release is an end-to-end Knowledge Management workflow with a retrieval-augmented generation (RAG) assistant for internal support staff and external customers. Access to knowledge and conversations must follow the approved role and tenant boundaries. External knowledge requires review and publication, and unanswered customer questions can be escalated to human support.

The project is for a learning/portfolio demonstration and uses synthetic data. The owner approved local development followed by a hosted Azure demo and selected the implementation stack and supporting architecture/services under DEC-041–DEC-052. Exact AI models/region, resource configuration, measurable service targets, and detailed API contracts remain open for their specified design stages.

## 3. Problem statement

The baseline describes a need for support agents to find approved information and prepare grounded responses. It proposes a broader portal with ticket intelligence, analytics, lookup tools, and AI-assisted workflows. For the first release, the owner selected a narrower knowledge-management and RAG slice rather than the broader ticket and analytics capabilities. This PRD describes that approved slice and keeps remaining baseline statements separate from approved scope.

## 4. Business objectives and success measures

| ID | Approved objective |
|---|---|
| BR-001 | Demonstrate a customer-support knowledge portal as a learning/portfolio project using synthetic data and production-minded engineering practices. |
| BR-002 | Help support agents locate approved information and prepare grounded responses, while retaining human responsibility for customer-facing decisions. |
| BR-003 | Demonstrate repeatable quality evaluation for retrieval, grounding, citations, structured outputs, tenant isolation, and core APIs. Measurable criteria must be defined before release approval. |
| BR-004 | Make setup, testing, monitoring, cost controls, and deployment reproducible for a demonstrable application. Numeric operating targets remain deferred. |
| BR-005 | Measure any reduction in search and routine reply-composition effort in a later pilot rather than claim an unverified benefit. No KPI, baseline, or target is approved. |

## 5. Scope

### 5.1 In scope — first demonstrable release

- Knowledge document upload, processing, lifecycle management, and RAG retrieval for the approved first-release slice.
- Uploaded files must not exceed 10 MB per file (10,000,000 bytes; DEC-055).
- Internal support staff and external customers as assistant audiences.
- Tenant- and role-scoped knowledge retrieval and conversation access.
- Internal knowledge management and external article review, approval, rejection, publication, and withdrawal for review.
- Grounded answers with source references, appropriate abstention when evidence is inadequate or conflicting, and human escalation for unanswered questions.
- Tenant membership and internal support staff provisioning by the Tenant Admin, within the approved role boundaries.
- Platform operations limited to approved platform-level operational metadata and without access to tenant business content.
- Synthetic data only.
- Local development/testing followed by a hosted Azure demonstration.
- English-only first-release support and basic accessibility practices.

### 5.2 Explicitly deferred from the first release

- Ticket list/detail, ticket summarization/classification, and advanced ticket intelligence.
- Simple dashboard and support analytics.
- Read-only ticket/customer lookup tools; knowledge search/retrieval remains in scope for RAG.
- Synthetic ticket taxonomy, fields, and seed strategy until ticket AI/analytics enter a future phase.
- GitHub issue/PR, CI, and delivery workflow requirements, which are deferred to the next phase.

### 5.3 Other baseline capabilities

Baseline capabilities not included in the approved first-release slice or the explicit deferrals above remain Draft/unprioritized. This PRD does not infer that they are either in scope or out of scope.

## 6. Stakeholders and user roles

| Role | Approved first-release responsibilities and boundaries |
|---|---|
| Tenant Admin | Manages tenant users/membership, knowledge sources, and knowledge content in the tenant. May create/edit external articles for Support Manager review but may not approve, reject, or publish them. |
| Support Agent | Creates, reads, and manages internal knowledge throughout the tenant and retrieves it across lifecycle statuses. May create/edit external articles for review but may not approve, reject, or publish them. By default, can retrieve published external knowledge in the tenant unless configured restrictions apply. May view/respond to escalated external-customer conversations. |
| Support Manager | Reviews, approves, rejects, and publishes external knowledge; retrieves all knowledge lifecycle statuses in the tenant; manages role/permission restrictions. |
| Platform Admin | Operates the platform using permitted platform-level operational metadata only. Must not access tenant-specific business content, customer data, tickets, knowledge articles, or uploaded documents. |
| External Customer | Uses the assistant with an authenticated account associated with a tenant. Tenant scope is derived server-side; the customer can access only their own conversation history under that account and tenant. |

Detailed registration/verification, invitation/approval, and role-restriction assignment workflows remain deferred.

## 7. First-release workflows

### 7.1 Knowledge ingestion and publication

1. A Support Agent uploads and manages a knowledge document.
2. The system validates and processes the document, records its lifecycle status, and makes authorized knowledge available for retrieval after processing.
3. A Tenant Admin or Support Agent may author/edit an external article for review.
4. A Support Manager or explicitly authorized higher-level role reviews the article and may approve, reject, publish, or withdraw it.
5. Only explicitly approved and published external articles are eligible for external-customer retrieval.
6. Outdated external articles are flagged and withdrawn from external access until updated and reapproved. Relevant changes are audit-logged.

### 7.2 Assistant response and escalation

1. An authenticated internal user or external customer submits a question.
2. Retrieval applies the user's role, tenant, and permission scope.
3. The assistant generates a response grounded in eligible knowledge and provides source references.
4. If evidence is missing, conflicting, stale, or insufficient, the assistant abstains rather than presenting an unsupported answer as verified.
5. The user can escalate an unanswered question to human support. A Support Agent may view/respond to escalated customer conversations without broadening the customer's access to other conversation history.

### 7.3 Tenant membership and operations

Tenant Admins manage tenant membership, including internal support staff invitations/provisioning, updates, and immediate deactivation/removal when access is no longer required. Membership changes are audit-logged and data access is limited to active tenant membership. Platform Admin operations remain limited to approved platform-level metadata.

## 8. Business requirements

The approved business requirements and success-measure limitations are listed in Section 4. There is no approved numeric KPI, performance target, cost ceiling, or later-pilot success threshold.

## 9. Functional requirements

| Requirement area | Approved first-release requirements |
|---|---|
| Customer assistant (`FR-CA-01`–`FR-CA-16`) | The baseline-derived assistant and knowledge-retrieval capabilities supporting the approved RAG slice; internal and external audiences; permission-scoped retrieval; approved/published-only external knowledge; source references; abstention; human escalation; server-derived external tenant scope; and per-account/tenant conversation-history isolation. |
| Knowledge management (`FR-KB-01`–`FR-KB-17`) | The baseline-derived ingestion and retrieval capabilities supporting the approved knowledge workflow, including a 10 MB maximum per uploaded file; Support Agent management of internal knowledge; role-bounded external article authoring and approval/publication; outdated-content review/withdrawal; configurable review timing with a 90-day default and per-article override. |
| Tenant operations (`FR-OP-09`–`FR-OP-14`) | Tenant Admin membership management and audit; configurable JWT expiry and token renewal/revocation support; local development followed by a hosted Azure demo; Azure SQL in both environments; JWT claims `UserId`, `UserName`, `Role`, and `exp` for authenticated users, with `TenantId` included for tenant-scoped users and omitted for Platform Admin; server-side validation of tenant and role where applicable. |
| RAG and evaluation (`AI-001`, `AI-002`) | Retrieve only authorized knowledge, preserve source references, abstain when evidence is inadequate/conflicting, and maintain tenant boundaries. Before release approval, detailed design must define evaluation datasets, measurable metrics, and acceptance thresholds. |
| Platform operations (`ROLE-004`, `RULE-010`–`RULE-011`) | Allow access to approved platform-level operational metadata only; prohibit access to tenant business content and customer data. |
| Deferred requirements | Ticket intelligence, agent-copilot features beyond the approved RAG assistant, analytics, ticket/customer lookup tools, and other remaining baseline-only capabilities are not promoted into the first-release scope unless separately approved. |

The project owner confirmed that the maximum upload size is 10 MB per file, resolving Q-033 after Gate 4 approval. Requirement `FR-KB-17` records this constraint; the original baseline remains unchanged.

## 10. Non-functional requirements

| ID / area | Approved condition |
|---|---|
| NFR-007 Accessibility | Follow basic practices including keyboard navigation, readable contrast, labels, and screen-reader-friendly controls. The WCAG conformance level remains open. |
| NFR-011 Localization | English only in the first release. |
| Security and tenant isolation | Enforce authentication, server-derived tenant isolation, role-based authorization, secure knowledge access, and consistent deletion across source and derived document data. Platform Admin access is prohibited from tenant business content. |
| AI/RAG release readiness | Define measurable evaluation metrics, datasets, and acceptance thresholds before release approval. |
| Service readiness | Define measurable latency, availability/recovery, concurrency, and operating-cost targets and conduct performance testing against them before release approval. No numeric values are set. |

Other source-derived non-functional statements remain Draft unless explicitly approved above. No WCAG conformance level, numeric service target, recovery objective, cost ceiling, or log-retention target is approved.

## 11. Business rules and AI guardrails

- Only explicitly approved and published external knowledge is available to external customers.
- External articles must be accurate, current, customer-friendly, free from confidential/sensitive/internal-only content, and must not expose another tenant's data.
- Outdated external articles are flagged and withdrawn until updated and reapproved; changes are audit-logged.
- Published external knowledge has a default 90-day review interval; Support Managers may set a different review date for an individual article. This is separate from document retention.
- Support Agents retrieve internal knowledge across lifecycle statuses within their tenant. Published external knowledge is available by default unless role/permission restrictions are configured by a Support Manager.
- Tenant Admins and Support Agents may author external content for review but cannot approve, reject, or publish it.
- Tenant access is derived from authenticated server-side identity and active membership; request parameters or headers cannot select/change tenant scope.
- External customers may access only conversations created under their authenticated account and associated tenant.
- Platform Admins may not access tenant business content.
- Membership changes are audit-logged.
- The assistant retrieves only authorized knowledge, provides source references, preserves tenant boundaries, and abstains when evidence is inadequate or conflicting.

Other baseline-only rules remain Draft as shown in the [requirements inventory](../analysis/requirements-inventory.md).

## 12. Data requirements

- Use fabricated organizations, users, knowledge, and evaluation assets only; do not use real customer data or secrets in prompts, logs, fixtures, or screenshots.
- Document retention is 90 days from original upload. At expiry, delete the source document, extracted text, chunks, and embeddings.
- Backup deletion and log/evaluation-record retention remain unresolved.
- External-customer conversation-history retention/deletion remains unresolved.
- The entities in the baseline are illustrative, not an approved schema. Field-level classification, migration, ownership, and lifecycle details beyond the requirements above are deferred.
- Synthetic ticket taxonomy, fields, and seed strategy are deferred with ticket AI/analytics.

## 13. Integration and technology constraints

| Decision / dependency | Status |
|---|---|
| Azure SQL for local-development and hosted environments | Approved at Gate 3 |
| Azure AI Foundry for answer generation and embeddings | Approved at Gate 3; exact models, region, deployment configuration, and cost envelope deferred |
| Identity backed by Azure SQL with JWT authentication | Approved at Gate 3; access-token expiry is configurable; first release has no refresh tokens and renews by reauthentication (DEC-051); user-wide Identity security-stamp validation revokes tokens (DEC-052); exact lifetime remains open under Q-026 |
| Detailed API contracts | Authentication, tenant isolation, role authorization, secure knowledge access, and consistent source/derived deletion requirements approved; endpoint paths, schemas, validation details, pagination, idempotency, and error formats deferred to solution/detailed design |
| .NET 10 / ASP.NET Core, React + TypeScript, Bootstrap, SQL Server/Azure SQL, Azure AI Foundry | Approved for implementation under DEC-041; EF Core approved under DEC-050; exact Foundry models, region, and deployment configuration remain open |
| Backend architecture | Modular monolith API with separate React application under DEC-044 |
| Search, source-document storage, background processing | Azure AI Search (DEC-045); Azure Blob Storage for local/hosted sources, with local Azure development storage (DEC-046/047); Azure Function triggered by Azure Service Bus (DEC-048), using a dedicated Azure development namespace locally (DEC-049). Account availability and resource/configuration details remain unverified; no provisioning is authorized. |
| Identity session design | Email/password sign-in (DEC-054); no refresh tokens initially; renew by reauthentication and revoke all of a user's tokens by Identity security-stamp validation (DEC-051/052). Internal users have active membership in one tenant only (DEC-053). Access-token lifetime remains configurable and undecided. |
| External ticketing/CRM/email/messaging integrations | Not part of the approved first-release slice |
| .NET 10 / ASP.NET Core, React + TypeScript, Bootstrap, other baseline services | Proposed or baseline-stated technology choices; not promoted to approved constraints unless separately recorded as approved |

## 14. Error and exception scenarios

- Failed or invalid document processing must not be presented as successful; processing status and errors should be visible. Detailed parser behavior, retry limits, and terminal failure handling are not defined.
- Insufficient, missing, stale, or conflicting retrieval evidence must result in abstention rather than an unsupported answer.
- Unauthorized cross-tenant, cross-role, or cross-customer access must be denied.
- Detailed API error shapes, model/search failure responses, and retry behavior remain for detailed design.

## 15. Risks, dependencies, and constraints

Key risks are cross-tenant leakage, inaccurate or overconfident model output, document parsing/indexing failures, cloud cost uncertainty, and operational metadata exposing tenant content. Key dependencies include Azure AI Foundry deployment availability/quota/compatibility, Azure SQL and supporting resource configuration, a background processing capability, and synthetic knowledge/evaluation assets. See the [risks and dependencies register](../analysis/risks-and-dependencies.md) for the full record.

## 16. Assumptions and open questions

### Approved constraints

- Synthetic/fabricated data only.
- Local development/testing followed by a hosted Azure demonstration.
- Azure SQL for local and hosted environments.
- Azure AI Foundry for generation and embeddings.
- English only in the first release.

### Open or deferred

- Backup deletion and log/evaluation-record retention; external conversation-history retention/deletion.
- Exact AI models, region, deployment configuration, quota/compatibility, and AI cost envelope.
- Evaluation datasets, metrics, and thresholds; numeric latency, availability/recovery, concurrency, and operating-cost targets.
- WCAG conformance level.
- API contract details and model/search failure handling.
- External-customer registration/verification; membership invitation/approval workflows; detailed role-restriction assignment.
- Azure AI Search, Blob Storage, and Function/Service Bus resource configuration, local account availability, and provisioning.
- Exact JWT access-token lifetime and database-check performance for Identity security-stamp revocation.
- Ticket data taxonomy/fields/seed strategy and delivery workflow requirements in their deferred phases.
- Full prioritization/disposition of remaining baseline-only requirements.
- A measurable KPI for the later pilot described by BR-005.
## 17. Requirements traceability

| Business requirement | Related approved requirements / trace |
|---|---|
| BR-001 | Synthetic-only data (`DATA-003`), role boundaries, approved first-release slice; stories US-001–US-007 |
| BR-002 | First-release assistant and knowledge-management requirements (`FR-CA-*`, `FR-KB-*`, `AI-001`); stories US-001–US-006; AC-001–AC-008, AC-014 |
| BR-003 | Evaluation requirement `AI-002`, security/tenant isolation, and core API invariants (`API-001`); AC-010 and AC-012 |
| BR-004 | Approved local-to-Azure environment, Azure SQL, membership/operational requirements, and API invariants; AC-010 and AC-013 |
| BR-005 | Later-pilot outcome only; no approved metric, target, or acceptance criterion |

The full approved story, acceptance-criteria, and requirement mapping is maintained in [requirements-traceability.md](../analysis/requirements-traceability.md). Test-case IDs and executable test designs have not been assigned.

## 18. Approval and sign-off

| Gate | Status |
|---|---|
| Gate 1 — initial baseline analysis | Approved for analysis accuracy and proceeding to discovery |
| Gate 2 — discovery findings | Approved as sufficiently complete to prepare the requirements package |
| Gate 3 — requirements package | Approved as presented; Draft/unprioritized items and unresolved/deferred decisions retain their statuses |
| Gate 4 — this PRD | Approved by the project owner; Q-033 was open at approval and was subsequently resolved under DEC-040; date not recorded |
| Gate 5 — implementation planning | Planning authorized and plan approved; implementation separately authorized under DEC-042 |

Gate 4 approval did not itself authorize implementation planning. Separate Gate 5 authorization was recorded under DEC-038 and the plan was approved under DEC-039. The project owner later authorized implementation under DEC-042.
