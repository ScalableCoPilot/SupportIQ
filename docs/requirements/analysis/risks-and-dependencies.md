# SupportIQ Initial Risks and Dependencies

## Status

Initial risks and external dependencies extracted from the draft baseline. Likelihood and impact ratings are not assigned because the source provides no rating scale or evidence to support numeric scoring. Mitigations listed below are source-stated controls or analysis observations, not proof that the risk is resolved.

## Risks

| ID | Risk | Source-stated handling / initial observation | Open point |
|---|---|---|---|
| RISK-001 | Cross-tenant leakage through filters, caching, or retrieval paths. | Owner confirmed tenant isolation and active-membership scoping; external tenant scope must derive from authenticated server-side identity, not request parameters/headers; membership changes must be audited. Baseline calls for centralized tenant scoping, API authorization, and negative integration tests. | Detailed registration/verification and restriction configuration workflows and complete path inventory remain to be defined. |
| RISK-002 | Model output may be inaccurate or overconfident. | Ground answers, cite sources, abstain when evidence is insufficient, evaluate, validate structured output, and require human review. Owner defined external-article quality/confidentiality criteria, outdated-content withdrawal/reapproval, review triggers, and a configurable 90-day default review interval. | Evaluation acceptance thresholds remain open. |
| RISK-003 | Document parsing/indexing may fail on complex files. | Validate supported files and size; surface processing status and safe errors; use retries. | Parser behavior, retry limits, and terminal failure handling are unspecified. |
| RISK-004 | Cloud costs may exceed the learning budget. | Use small datasets, caps, alerts, and teardown instructions. | No numeric operating-cost target is confirmed; define measurable targets during detailed design and performance testing before release approval. |
| RISK-005 | First-release scope may be too broad for the suggested intensive 30-day build. | Owner selected knowledge management plus a RAG assistant as the must-have vertical slice and explicitly deferred ticket list/detail, summary/classification, simple dashboard/analytics, and read-only ticket/customer lookup. | Detailed invitation/approval workflows and non-knowledge permissions for out-of-scope capabilities are deferred; the 30-day target is suggested, not approved. |
| RISK-006 | Deployment and data-service expectations differ between local-first project guidance and cloud deployment described in the baseline. | Owner confirmed local development/testing followed by a hosted Azure demo and Azure SQL for both environments. | Cloud-resource/cost details remain open under Q-012; measurable latency, availability/recovery, concurrency, and operating-cost targets must be defined during detailed design and performance testing before release approval. |
| RISK-007 | Serving both internal staff and external customers may lead to inappropriate data exposure or communication behavior if their access boundaries differ but are not defined. | Owner confirmed external knowledge quality/confidentiality boundaries, explicit approval/publication, and outdated-content withdrawal/reapproval triggers; customers use authenticated tenant binding and may access only their own conversations; Support Agents handle escalated customer conversations. | Registration/verification workflows and conversation-history retention/deletion rules remain unresolved or deferred; ensure escalation handling does not broaden unrelated conversation-history access; article review interval is separately configurable from data retention. |
| RISK-008 | Platform troubleshooting may expose tenant content through logs, metrics, configuration, or audit views. | Owner permits specified platform-level metadata only and prohibits exposing tenant content, customer data, tickets, knowledge articles, or uploaded documents. | Ensure allowed views remain platform-level or aggregated and do not leak tenant content; detailed operational field rules remain to be validated. |

## Dependencies

| ID | Dependency | Evidence | Status / impact |
|---|---|---|---|
| DEP-001 | Azure AI Foundry answer-generation model/deployment and embedding model/deployment availability, region, quota, price, dimensions, and compatibility. | Baseline open question and technology architecture; owner selected Azure AI Foundry for answer generation and embeddings under Q-007 and deferred model, region, and cost-envelope decisions to detailed design. | Provider confirmed for both functions; exact models, region, and cost envelope deferred; deployment configuration, availability, quota, and compatibility remain unconfirmed; affects AI feasibility and cost. |
| DEP-002 | Azure AI Search, Azure SQL, and Blob Storage availability and configuration. | Baseline technology and architecture sections; Azure SQL environment arrangement confirmed under Q-005. | Azure SQL selected for both local-development and hosted environments; AI Search/Blob Storage availability and resource configuration remain unconfirmed. |
| DEP-003 | Background processing capability for extraction, chunking, embedding, indexing, and retries. | Baseline names background worker / Azure Functions. | Named in architecture, but service choice is not approved. |
| DEP-004 | Synthetic knowledge, tickets, tenant organizations, users, and evaluation examples. | Baseline sample data and evaluation assets. | Ticket taxonomy, fields, and seed strategy are deferred until ticket AI/analytics enter a future phase; other sample volumes remain proposals. |
| DEP-005 | Project-owner review at Gate 1, discovery agreement at Gate 2, requirements approval at Gate 3, PRD approval at Gate 4, and separate planning authorization at Gate 5. | Repository instructions and requirements-analysis process. | Process dependency; no later gate is presumed approved. |
| DEP-006 | GitHub Actions, repository issue/PR workflow, and any deployment credentials/resources if cloud deployment remains in scope. | Baseline delivery workflow and architecture. | Owner deferred issue/PR, CI, and delivery workflow requirements to the next phase; no first-release workflow scope was specified. |

## Items requiring further evidence

No cost estimate, service quota evidence, performance baseline, tenant-isolation test evidence, or stakeholder approval evidence is present in the sources reviewed. These remain unverified rather than assumed.
