# SupportIQ Baseline Analysis

## Document status

- Analysis stage: Phase 1 — Project understanding and source analysis
- Review gate: Gate 1 — Initial baseline analysis review
- Status: Gate 1 approved; Gate 2 stakeholder discovery in progress
- Source baseline: [SupportIQ-Baseline.md](../baseline/SupportIQ-Baseline.md)
- Original baseline: Preserved unchanged

## Project overview

SupportIQ is described as a learning/portfolio demonstration of an AI-powered customer-support knowledge portal for the fictional B2B SaaS provider CloudDesk. The draft aims to help support teams find approved knowledge, work with tickets, prepare grounded response drafts, and evaluate and operate AI-assisted workflows. It specifies synthetic data and production-minded engineering practices, but explicitly says it is not a commitment to production readiness.

The system is intended to combine a tenant-aware knowledge base, document ingestion, retrieval-augmented generation (RAG), ticket intelligence, agent assistance, limited workflow automation, and evaluation/operational monitoring. AI output is assistive; people retain responsibility for customer-facing decisions and communications.

## Source document inventory

| Source | Role in this analysis | Status and use |
|---|---|---|
| [SupportIQ-Baseline.md](../baseline/SupportIQ-Baseline.md) | Original product baseline, including draft scope, capabilities, roles, workflows, architecture, acceptance criteria, risks, assumptions, and questions | Primary source; treated as evidence, not approved requirements |
| [analyze-requirements.prompt.md](../../../.github/prompts/analyze-requirements.prompt.md) | Requested analysis workflow and expected initial response | Process instruction; not product evidence |
| [copilot-instructions.md](../../../.github/copilot-instructions.md) | Repository context, proposed technology defaults, source precedence, and approval rules | Supporting project instruction; proposals remain proposals |
| [GEMINI.md](../../../GEMINI.md) | Project approval gates, documentation rules, and development constraints | Supporting project instruction; does not approve baseline requirements |
| [requirements-analysis skill](../../../.github/skills/requirements-analysis/SKILL.md) | Lifecycle, classification, evidence, discovery, and approval method | Process guidance |

No other Markdown documents were present under `docs/requirements/` at the start of this analysis. The baseline file is the only identified source in `docs/requirements/baseline/`.

## Initial baseline summary

### Business purpose and outcomes stated in the baseline

- Demonstrate an end-to-end AI application using synthetic data and a production-minded approach.
- Help support agents find approved information and prepare grounded replies.
- Summarize and classify tickets, recommend knowledge, and abstain when evidence is insufficient.
- Establish repeatable testing for retrieval, grounding, citations, structured output, tenant isolation, and core APIs.
- Demonstrate setup, CI, monitoring, cost controls, and a deployable application.
- Treat reduced search and reply-composition time as an outcome for later measurement, not an already demonstrated benefit.

### Users and roles listed

- Tenant Admin: manage tenant users, settings, and knowledge sources.
- Support Agent: search permitted knowledge, view tickets, use AI suggestions, and provide feedback.
- Support Manager: review team queues, escalations, quality, and analytics; assignment authority is qualified by “where authorized.”
- Platform Admin: operate the platform with audited, least-privilege access to approved platform metadata and operational information only; no tenant business-content access.

The baseline says authorization must be enforced by APIs, not only by UI controls. Roles may be seeded for the demonstration but must be explicit and testable.

### First demonstrable release scope stated

- Authentication-ready structure and tenant-aware authorization.
- Knowledge upload, extraction, chunking, embedding, indexing, status, reindex, and deletion.
- RAG chat with conversation context, citations, no-answer behavior, and feedback.
- Ticket list/detail, AI classification and summarization.
- Agent copilot for suggested replies and knowledge recommendations, with human review.
- Read-only customer/ticket lookup tools with audited execution.
- Automated tests, GitHub issue/PR workflow, CI, telemetry, and Azure deployment.

The baseline marks arbitrary text-to-SQL, unsupervised communication, complex autonomous orchestration, production integrations, SSO, billing, multi-region recovery, compliance certifications, large-scale benchmarking, custom fine-tuning, and automated model selection as deferred or optional.

### Functional capability groups

The baseline assigns identifiers to functional requirements in these groups:

- Customer assistant: `FR-CA-01`–`FR-CA-08`.
- Knowledge management: `FR-KB-01`–`FR-KB-08`.
- Ticket intelligence: `FR-TK-01`–`FR-TK-07`.
- Agent copilot: `FR-AC-01`–`FR-AC-07`.
- Workflow automation/tools: `FR-WF-01`–`FR-WF-06`.
- Support analytics: `FR-AN-01`–`FR-AN-05`.
- AI evaluation/testing: `FR-EV-01`–`FR-EV-06`.
- Security and AI operations: `FR-OP-01`–`FR-OP-08`.

The detailed source wording is summarized and indexed in [requirements-inventory.md](requirements-inventory.md). Existing source IDs are retained.

### Baseline constraints and boundaries explicitly stated

- Synthetic/fabricated data only; do not use real customer records or secrets in prompts, logs, fixtures, or screenshots.
- Maximum upload size is stated as 10 MB per file; document retention is stated as 90 days.
- Platform administrators must not access tenant business content.
- The first release must not send customer-facing messages automatically.
- Arbitrary SQL, shell commands, and unrestricted network access are prohibited for model tools.
- Business-data changes require explicit human confirmation; write actions may be deferred.
- The API mediates model/search access; provider credentials must not be exposed to the browser.
- Endpoint names and logical entities are illustrative, not finalized contracts or schema.
- The baseline labels its requirements draft and says assumptions should be validated before implementation.

### Technical choices stated in sources

The baseline names React + TypeScript, .NET 10 / ASP.NET Core, Azure AI model endpoint, Azure AI Search, Azure SQL, Blob Storage, App Service, Key Vault, Application Insights, and GitHub Actions. It also says the backend uses ASP.NET Core Identity with a local SQL database and JWT, but the JWT wording is masked in the document as `******`. The project owner later confirmed Azure SQL for both local-development and hosted environments (Q-005), resolving the environment arrangement without changing the original baseline.

Repository instructions list proposed defaults including React + TypeScript, .NET 10 / ASP.NET Core, Bootstrap, SQL Server, local database identity with JWT, Azure AI Foundry, and local development initially. These are proposals unless approved. Potential environment and service distinctions are recorded in [gap-analysis.md](gap-analysis.md) and [open-questions.md](../evidence/open-questions.md), not silently resolved here.

## Initial status assessment

The baseline is titled as a PRD, has a version/date, and includes a “Confirmed Baseline Decisions” table; however, its document-control status says “Draft baseline,” calls for assumptions to be validated, and does not contain a stakeholder sign-off record. Accordingly:

- The statements are source-supported baseline content.
- The table’s “confirmed” label is preserved as the baseline’s own label, not treated as proof of stakeholder approval in this analysis.
- All extracted requirements remain Draft/Under Review until reviewed through the project’s approval gates.
- Gate 1 concerns the accuracy of this initial analysis; Gate 1 approval would not by itself approve the full requirements package.

## Gate 1 review outcome

The project owner confirmed that this analysis accurately represents the baseline and its unresolved areas and approved proceeding to Gate 2. This approval applies only to the initial analysis and does not approve any individual requirement, assumption, technical choice, or unresolved decision. The owner asked that all identified gaps, assumptions, risks, dependencies, and open questions remain documented.

The original baseline remains unchanged. Discovery is now in progress; no PRD or implementation plan is being produced at this stage.

## Gate 2 discovery findings to date

- The project owner confirmed that both internal support staff and external customers are intended users of the assistant in the first release. This is a confirmed stakeholder statement, not approval of the complete requirements.
- The project owner confirmed the delivery sequence is local development and testing followed by a hosted Azure demo. This is a confirmed stakeholder statement, not approval of the complete requirements.
- The project owner selected Azure AI Foundry for answer generation and embeddings. Exact model, region, and cost-envelope decisions are deferred to detailed design; deployment configuration remains open. This is a confirmed stakeholder statement, not approval of the complete requirements.
- The project owner confirmed that external customers may retrieve publicly approved knowledge only. This is a confirmed stakeholder statement, not approval of the complete requirements.
- The project owner confirmed that a Support Manager or explicitly authorized higher-level role is responsible for external knowledge approval, and that only approved and published knowledge is available externally. This is a confirmed stakeholder decision, not approval of the complete requirements.
- The project owner confirmed the Platform Admin boundary is categorical: no access to tenant business content. This aligns with the baseline. The owner specified the permitted platform-level metadata and operational diagnostics under Q-015.
- The project owner specified that Platform Admin may access platform-level operational metadata only: system health, application logs, service status, usage metrics, configuration, audit logs, and aggregated platform statistics. These views must not expose tenant-specific business content, customer data, tickets, knowledge articles, or uploaded documents.
- The project owner selected end-to-end Knowledge Management with a RAG-based AI Assistant as the must-have first-release vertical slice: Support Agent upload/management; Support Manager or authorized-role approval for external use; grounded answers from approved knowledge for internal staff and external customers according to their respective permissions; and escalation of unanswered questions to human support.
- Support Agents may view and respond to external customer conversations escalated to human support.
- The owner placed advanced ticket intelligence, analytics, and additional AI tools in later phases, and explicitly deferred the baseline ticket list/detail, ticket summary/classification, simple dashboard, and read-only lookup tools from release one. Synthetic ticket taxonomy, fields, and seed strategy are also deferred until ticket AI and analytics are included in a future phase. Knowledge search/retrieval for the RAG assistant remains in the first-release slice.
- Support Agents may retrieve internal knowledge and, by default, published external knowledge within their own tenant unless role- or permission-based restrictions are configured. Support Managers manage support operations and knowledge article review, approval, rejection, and publication; they may manage access restrictions and retrieve all knowledge in their tenant, including draft, pending-review, approved, rejected, and published articles. Tenant isolation must always be enforced; Platform Admins may not access tenant knowledge.
- Support Agents may create, read, and manage any internal knowledge in their tenant, independent of uploader, and may retrieve it in all lifecycle statuses. External article approval/publication remains with Support Managers or explicitly authorized higher-level roles.
- Support Agents may create and edit external knowledge articles for Support Manager review, but may not approve, reject, or publish those articles.
- Tenant Admins may also create and edit external knowledge articles for Support Manager review, but may not approve, reject, or publish those articles.
- Detailed restriction assignment, invitation, and approval workflow details may be finalized during design. No additional first-release role/permission boundaries were requested; non-knowledge permissions for out-of-scope capabilities are deferred.
- Tenant Admin manages tenant membership by inviting/assigning users, updating membership and role permissions, and immediately removing/deactivating access when no longer required. Higher-level roles may perform these actions only when explicitly authorized. Users may access only data for their active tenant membership, and all membership changes must be recorded in audit logs. Detailed invitation and approval workflows may be finalized during design.
- External customer accounts use Identity backed by Azure SQL with JWT and are associated with a tenant during registration or invitation. Tenant scope is derived server-side from authenticated identity and may not be selected or changed via request parameters or headers. Detailed registration and verification workflows may be finalized during design.
- External customers may access only conversation history created under their authenticated account and associated tenant; they may not access another customer's or internal staff's conversations. History retention and deletion policies may be finalized during detailed design.
- External knowledge articles must be accurate, current, customer-friendly, free from confidential/sensitive/internal-only information, and must not expose another tenant's data. Only articles explicitly approved and published by the Support Manager or an explicitly authorized role may be accessed.
- Once identified as outdated, an external article is flagged for review and temporarily withdrawn until updated and reapproved by the Support Manager or explicitly authorized role; all changes must be audit-logged. Flag review when the review date expires, content becomes inaccurate, a related product/process changes, a user reports an issue, or a Support Manager flags it manually.
- Published external knowledge has a configurable default review interval of 90 days; Support Managers may set a different review date for individual articles. This is separate from the baseline's 90-day document-retention period.
- Stakeholder follow-up clarified that the document-retention period starts on the original upload date; after 90 days, the source document, extracted text, chunks, and embeddings must be deleted. Backup deletion and log/evaluation-record retention remain open for detailed design and compliance review.
- The project owner deferred all first-release AI/RAG evaluation thresholds, including retrieval quality, grounding, citation correctness, abstention, and prompt-injection handling. Measurable metrics, evaluation datasets, and acceptance thresholds must be defined during AI/RAG detailed design before release approval.
- No numeric demo targets are confirmed for latency, availability/recovery, concurrency, or operating cost. Measurable targets must be defined during detailed design and performance testing before release approval.
- The project owner confirmed English-only first-release support and basic accessibility practices (keyboard navigation, readable contrast, labels, and screen-reader-friendly controls); WCAG conformance level remains open for detailed design.
- The owner deferred detailed API schemas, endpoint paths, validation rules, pagination, idempotency, and error-response formats to solution/detailed design. Requirements must confirm authentication, tenant isolation, role-based authorization, secure knowledge access, and consistent source/derived document deletion.
- JWT access-token expiry, renewal, and revocation must be configurable. Exact lifetime and refresh-token use are deferred to detailed design based on security requirements, session management, and user experience.
- JWTs must include UserId, UserName, TenantId, Role, and expiration (`exp`) claims. TenantId and Role must be validated server-side for authorization; additional permission/claim details may be finalized during design.
- External-customer registration/verification workflow, conversation-history retention/deletion, backup deletion, log/evaluation-record retention, and differences between the customer-facing and internal experiences remain open or deferred.

## Gate 2 review outcome

The project owner approved the discovery findings as sufficiently complete to prepare a requirements package for Gate 3 review. This is not approval of individual requirements or the complete requirements set. No PRD has been finalized, and implementation planning has not been authorized.

## Gate 3 requirements approval outcome

The project owner approved the requirements package as presented. Requirements explicitly marked Approved at Gate 3 are approved; baseline-only statements retained as Draft/unprioritized and unresolved/deferred decisions retain those statuses. A PRD may now be prepared for Gate 4 review. Gate 4 PRD approval and Gate 5 implementation-planning authorization are still required.
