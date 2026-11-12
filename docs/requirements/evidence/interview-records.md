# SupportIQ Interview Records

## Status

Discovery record. Stakeholder statements are recorded as given and are not generalized into product requirements or decisions without explicit validation.

## Gate 1 — Initial baseline analysis review

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Does the initial analysis accurately represent the baseline and its unresolved areas, or what corrections should be made before proceeding?
- **Response:** “Gate 1 approved. The initial baseline analysis accurately represents the SupportIQ baseline and its unresolved areas. Proceed to Gate 2 — Stakeholder Discovery. Please retain all identified gaps, assumptions, risks, dependencies, and open questions in their respective documentation. Do not treat this Gate 1 approval as approval of the individual requirements or unresolved decisions. Start stakeholder discovery by asking me the single most important clarification question. Wait for my response before asking the next question. Continue following the requirements-analysis skill and all approval gates.”
- **Recorded outcome:** Gate 1 approved; proceed to Gate 2. The approval is limited to the accuracy of the initial analysis and the transition to discovery. It does not approve individual requirements, assumptions, risks, technical choices, or unresolved decisions.
- **Related records:** Q-001 marked resolved as a Gate 1 process question; Q-002 is the first Gate 2 discovery question. See [open-questions.md](open-questions.md).

## Gate 2 — Assistant audience

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Who is the assistant’s intended primary user for the first release: internal support staff only, external customers, or both?
- **Response:** “Both internal staff and external customers.”
- **Recorded finding:** Both groups are intended users of the first-release assistant. This confirms the audience statement only; it does not define or approve either group’s permissions, identity, data scope, or experience.
- **Related records:** Q-002 answered; candidate `FR-CA-09` and ROLE-005 recorded as Confirmed but not Approved; Q-016 added to clarify customer-answer data scope. See [open-questions.md](open-questions.md).

## Gate 2 — External-customer knowledge scope

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** What knowledge should an external customer be able to retrieve through the assistant?
- **Response:** “Publicly approved knowledge only.”
- **Recorded finding:** External-customer assistant retrieval is limited to publicly approved knowledge. This does not identify who approves knowledge or define the publication workflow.
- **Related records:** Q-016 answered; candidate `FR-CA-10` recorded as Confirmed but not Approved; Q-009 asks who approves knowledge for external access. See [open-questions.md](open-questions.md).

## Gate 2 — External knowledge approval and Platform Admin access

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Who is responsible for approving knowledge before it becomes available to external customers?
- **Response:** “External knowledge approval will be handled by the **Support Manager or an explicitly authorized higher-level role**. Platform Admin will not automatically have access to tenant-specific knowledge content. Only approved and published knowledge can be accessed by external customers. Update the requirements and evidence documents accordingly.”
- **Recorded finding:** Approval responsibility is assigned to a Support Manager or explicitly authorized higher-level role. External customers can access only knowledge that is approved and published. The owner also stated Platform Admin has no automatic access to tenant-specific knowledge. This initially left the exact boundary open; the owner later confirmed a categorical prohibition in the response to Q-017 below.
- **Related records:** Q-009 answered; `FR-CA-11`, `RULE-009`, `RULE-010`, DEC-001, and DEC-002 recorded. Q-017 asks whether the baseline's Platform Admin prohibition remains categorical. See [open-questions.md](open-questions.md).

## Gate 2 — Platform Admin tenant-content boundary

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Does the baseline’s prohibition on Platform Admin access to all tenant business content remain categorical, or may an explicitly authorized Platform Admin access tenant-specific knowledge?
- **Response:** “Categorical prohibition: no access to tenant business content.”
- **Recorded finding:** Platform Admins are categorically prohibited from accessing tenant business content. This confirms and preserves the baseline boundary; it does not define the exact platform metadata or operational diagnostics they may access.
- **Related records:** Q-017 answered; RULE-010 and DEC-002 updated. Q-015 was subsequently answered in the next record. See [open-questions.md](open-questions.md).

## Gate 2 — Permitted Platform Admin metadata

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** What platform-level metadata and operational information should Platform Admins be allowed to access?
- **Response:** “Platform Admin may access platform-level operational metadata only, including system health, application logs, service status, usage metrics, configuration, audit logs, and aggregated platform statistics. Access must not expose tenant-specific business content, customer data, tickets, knowledge articles, or uploaded documents.”
- **Recorded finding:** Permitted categories are system health, application logs, service status, usage metrics, configuration, audit logs, and aggregated platform statistics. None may expose tenant-specific business content or customer/ticket/knowledge/document content.
- **Related records:** Q-015 answered; ROLE-004 and RULE-011 updated; DEC-003 recorded. See [open-questions.md](open-questions.md).

## Gate 2 — Must-have first-release vertical slice

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Which single end-to-end capability should be the must-have core of the first demonstrable release?
- **Response:**
  > The must-have vertical slice should be end-to-end Knowledge Management with a RAG-based AI Assistant:
  >
  > 1. Support Agent uploads and manages knowledge documents.
  > 2. Support Manager reviews and approves knowledge for external use.
  > 3. AI Assistant retrieves relevant approved knowledge and generates grounded answers.
  > 4. Internal Staff and External Customers receive answers based on their respective access permissions.
  > 5. Users can escalate unanswered questions to human support.
  >
  > Keep advanced ticket intelligence, analytics, and additional AI tools as later-phase capabilities.
- **Recorded finding:** The must-have vertical slice and later-phase exclusions are confirmed by the owner. A later response to Q-020 explicitly deferred the baseline's basic ticket list/detail, summary/classification, simple dashboard, and read-only lookup tools.
- **Related records:** Q-003 answered; FR-KB-09, FR-CA-12, FR-CA-13, and DEC-004 recorded. Q-020 clarifies the capability boundary. See [open-questions.md](open-questions.md).

## Gate 2 — Baseline capability deferrals

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Should the baseline’s basic ticket list/detail, summary/classification, simple dashboard, and read-only lookup tools also be deferred, or which should remain in the first release?
- **Response:**
  > Defer all four capabilities from the first release:
  > - Ticket list/detail
  > - Ticket summary/classification
  > - Simple dashboard
  > - Read-only lookup tools
  >
  > Focus the first release on knowledge ingestion, Support Manager approval, secure RAG retrieval, and AI-assisted answers for Internal Staff and External Customers. These capabilities can be considered for later phases.
- **Recorded finding:** All four listed baseline capabilities are deferred from release one. Knowledge retrieval for the RAG assistant remains in the first-release scope. Internal staff knowledge permissions were clarified in the subsequent Q-021 response.
- **Related records:** Q-020 answered; DEC-005 and the deferred-capability mapping in [requirements-inventory.md](../analysis/requirements-inventory.md) updated. Q-021 records internal retrieval scope. See [open-questions.md](open-questions.md).

## Gate 2 — Internal staff knowledge access

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** What knowledge may internal Support Agents and Support Managers retrieve in the first release?
- **Response:** Support Agents may retrieve internal knowledge and published external knowledge relevant to their roles. Support Managers may retrieve all knowledge statuses within their own tenant, including draft, pending-review, approved, rejected, and published content. Tenant isolation must always be enforced, and Platform Admins must not access tenant knowledge.
- **Recorded finding:** Support Agent access is limited to internal knowledge in all lifecycle statuses and, by default, published external knowledge within their own tenant unless role- or permission-based restrictions are configured. Q-008 later clarified that all internal knowledge statuses are accessible. Support Managers may retrieve every knowledge status within their tenant. Tenant isolation is mandatory, and the categorical Platform Admin restriction remains.
- **Related records:** Q-021 answered; candidate FR-CA-13, ROLE-002, ROLE-003, RULE-012, and DEC-006 recorded as confirmed but not approved. Q-022 clarifies default external-knowledge access and manager-configured restrictions; Q-008 later specified the Support Agent internal-status scope. See [open-questions.md](open-questions.md).

## Gate 2 — Support Agent published knowledge restrictions

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** What determines whether published external knowledge is relevant to a particular Support Agent's role for retrieval?
- **Response:** “Published external knowledge should be available to all Support Agents within their own tenant by default, unless specific role-based or permission-based restrictions are configured. Support Managers can manage these restrictions. Tenant isolation must always be enforced. Detailed assignment rules can be finalized during detailed design.”
- **Recorded finding:** All published external knowledge within a tenant is available to its Support Agents by default. Support Managers may configure role- or permission-based restrictions; tenant isolation remains mandatory. The owner deferred detailed assignment rules to detailed design.
- **Related records:** Q-022 answered; FR-CA-13, ROLE-002, RULE-012, and DEC-007 updated as confirmed but not approved. Tenant membership lifecycle remains open under Q-023. See [open-questions.md](open-questions.md).

## Gate 2 — Tenant membership lifecycle

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** How should a user's membership in a tenant be provisioned, changed, and revoked?
- **Response:** Tenant membership is managed by the Support Manager or an explicitly authorized higher-level role. Users are invited or assigned to the appropriate tenant; membership and role permissions are updated when required; membership is removed or deactivated immediately when access is no longer required. Users may access only data belonging to their active tenant membership, and all membership changes must be recorded in audit logs. Detailed invitation and approval workflows can be finalized during design.
- **Recorded finding:** Membership management authority, lifecycle actions, active-membership data scope, and audit logging are confirmed. Invitation and approval workflow details are deferred to design.
- **Related records:** Q-023 answered; candidate FR-OP-09, ROLE-001, RULE-013, and DEC-008 recorded as confirmed but not approved. Q-028 subsequently clarified that Tenant Admin is responsible for membership management, with higher-level delegation only when explicitly authorized. Q-024 clarified external customer identity and tenant association. See [open-questions.md](open-questions.md).

## Gate 2 — Tenant Admin and Support Manager responsibilities

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Should the Tenant Admin retain the baseline permissions to manage tenant users and knowledge sources, or should those permissions belong to Support Managers or explicitly authorized higher-level roles?
- **Response:** Tenant Admin retains responsibility for managing tenant users, tenant membership, and knowledge sources. Support Manager manages support operations and knowledge article review, approval, rejection, and publication. Higher-level roles may perform these actions only when explicitly authorized. Platform Admin must not access tenant business content.
- **Recorded finding:** Tenant Admin is responsible for tenant users, membership, and knowledge sources. Support Manager is responsible for support operations and knowledge lifecycle review/approval/rejection/publication. Higher-level roles require explicit authorization; the Platform Admin prohibition remains categorical.
- **Related records:** Q-028 answered; FR-KB-09, FR-OP-09, ROLE-001, ROLE-003, RULE-013, RULE-016, DEC-013 updated as confirmed but not approved. Q-029 asks about external approval criteria. See [open-questions.md](open-questions.md).

## Gate 2 — External customer identity and tenant binding

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** How should an external customer be identified and associated with the tenant whose published knowledge they may access?
- **Response:** External customers authenticate using the application's local database Identity with JWT-based authentication. Each customer account must be explicitly associated with a tenant during registration or invitation. The application determines tenant scope from the authenticated user's server-side identity and enforces tenant isolation. Customers must not be allowed to select or change their tenant through request parameters or headers. Detailed registration and verification workflows can be finalized during design.
- **Recorded finding:** Customer authentication uses Identity with JWT. Tenant association is explicit and server-side; request parameters or headers cannot select or change tenant scope. Q-005 later clarified that Identity is backed by Azure SQL in both local-development and hosted environments. Registration and verification workflows are deferred to design.
- **Related records:** Q-024 answered; candidate FR-CA-14, ROLE-005, RULE-014, and DEC-009 recorded as confirmed but not approved. Q-005 clarified the database service arrangement. Q-006 remains partially answered; token details remain open. Q-025 subsequently clarified external conversation-history access. See [open-questions.md](open-questions.md).

## Gate 2 — External customer conversation history

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** What conversation history, if any, may an external customer access through the assistant?
- **Response:** External customers may access their own conversation history only, limited to conversations created under their authenticated account and associated tenant. They must never access another customer's conversations or internal staff conversations. Conversation history retention and deletion policies can be finalized during detailed design.
- **Recorded finding:** External history access is limited to the authenticated customer account and associated tenant; other customers' and internal staff's conversations are prohibited. Retention and deletion are deferred to detailed design.
- **Related records:** Q-025 answered; candidate FR-CA-15 and RULE-015 recorded as confirmed but not approved. Q-026 subsequently recorded that token lifetime is deferred to design and expiry must be configurable. See [open-questions.md](open-questions.md).

## Gate 2 — JWT access-token lifetime

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** What lifetime should JWT access tokens have for authenticated users?
- **Response:** “Not decided yet. JWT access-token lifetime will be finalized during detailed design based on security requirements and user experience. The implementation must support configurable token expiry.”
- **Recorded finding:** No token lifetime is selected at this stage. Configurable JWT access-token expiry is required; the specific value is deferred to detailed design.
- **Related records:** Q-026 answered; candidate FR-OP-10 recorded as confirmed but not approved. Q-027 subsequently deferred the refresh-token choice to design and confirmed configurable renewal/revocation. See [open-questions.md](open-questions.md).

## Gate 2 — Refresh-token decision

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Should the application issue refresh tokens in addition to JWT access tokens?
- **Response:** “Defer this decision to detailed design. Evaluate refresh tokens based on security requirements, session management, and user experience. The authentication design should support configurable token renewal and revocation.”
- **Recorded finding:** Whether to use refresh tokens is deferred to detailed design. Configurable token renewal and revocation are required.
- **Related records:** Q-027 answered; candidate FR-OP-11 recorded as confirmed but not approved. Q-028 subsequently clarified Tenant Admin and Support Manager responsibilities. See [open-questions.md](open-questions.md).

## Gate 2 — Tenant Admin and Support Manager responsibilities

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Should the Tenant Admin retain the baseline permissions to manage tenant users and knowledge sources, or should those permissions belong to Support Managers or explicitly authorized higher-level roles?
- **Response:** Tenant Admin retains responsibility for managing tenant users, tenant membership, and knowledge sources. Support Manager manages support operations and knowledge article review, approval, rejection, and publication. Higher-level roles may perform these actions only when explicitly authorized. Platform Admin must not access tenant business content.
- **Recorded finding:** Tenant Admin is responsible for tenant users, membership, and knowledge sources. Support Manager is responsible for support operations and knowledge lifecycle review/approval/rejection/publication. Higher-level roles require explicit authorization; the Platform Admin prohibition remains categorical.
- **Related records:** Q-028 answered; FR-KB-09, FR-OP-09, ROLE-001, ROLE-003, RULE-013, RULE-016, and DEC-013 updated as confirmed but not approved. Q-029 asks about external approval criteria. See [open-questions.md](open-questions.md).

## Gate 2 — External knowledge approval criteria

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** What criteria must a Support Manager use when approving or publishing knowledge for external customer access?
- **Response:** Articles must be accurate, up to date, customer-friendly, and free from confidential, sensitive, or internal-only information. They must not expose another tenant's data. Only articles explicitly approved and published by the Support Manager or an authorized role can be accessed by external customers.
- **Recorded finding:** External articles must meet accuracy, freshness, customer-friendliness, confidentiality, and tenant-isolation criteria. Access requires explicit approval and publication by the Support Manager or an explicitly authorized role. Q-030/Q-031 later defined outdated-content withdrawal and review triggers; the default review interval remains open.
- **Related records:** Q-029 answered; FR-KB-09, RULE-017, and DEC-014 recorded as confirmed but not approved. Q-030 subsequently defined withdrawal/reapproval of outdated content; Q-031 asks what triggers outdated status. See [open-questions.md](open-questions.md).

## Gate 2 — Handling outdated published articles

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** What should happen to an already-published external article when it is no longer up to date?
- **Response:** Outdated articles should be flagged for review and temporarily withdrawn from external access until updated and reapproved by the Support Manager or an authorized role. All changes must be audit-logged.
- **Recorded finding:** Once identified as outdated, an external article is flagged and removed from external access until updated and reapproved by the Support Manager or explicitly authorized role. All related changes must be recorded in audit logs.
- **Related records:** Q-030 answered; candidate FR-KB-10 and RULE-018 recorded as confirmed but not approved. Q-031 defined review triggers and Q-032 set a 90-day default with per-article review-date override. See [open-questions.md](open-questions.md).

## Gate 2 — External knowledge review triggers

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** What should trigger an external knowledge article to be flagged as outdated for review?
- **Response:** Flag an article for review when its review date expires, its content becomes inaccurate, a related product or process changes, or a user reports an issue. Support Managers should also be able to manually flag articles. Review frequency can be configurable.
- **Recorded finding:** Review triggers include review-date expiry, inaccuracy, related product/process changes, user reports, and Support Manager manual flags. Review frequency must be configurable; Q-032 later established a default 90-day interval with per-article override.
- **Related records:** Q-031 answered; candidate FR-KB-11 and RULE-019 recorded as confirmed but not approved. Q-032 established the default review interval. See [open-questions.md](open-questions.md).

## Gate 2 — Default external knowledge review interval

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** What default review interval should apply to published external knowledge articles?
- **Response:** “Use a default review interval of 90 days for published external knowledge articles. Support Managers can configure a different review date for individual articles.”
- **Recorded finding:** Published external articles have a 90-day default review interval. Support Managers may configure an individual article's review date. This is separate from the baseline's 90-day document-retention period.
- **Related records:** Q-032 answered; candidate FR-KB-12 and RULE-020 recorded as confirmed but not approved. Q-010 remains open for document retention timing and scope. See [open-questions.md](open-questions.md).

## Gate 2 — Local-first deployment sequence

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Is the intended initial deliverable local-only, a hosted Azure demo, or a local build followed by a hosted demo?
- **Response:** “Local build first, followed by a hosted Azure demo. This allows initial development and testing locally before deploying the demonstrable release to Azure.”
- **Recorded finding:** Development and testing occur locally first; the demonstrable release is then deployed as a hosted Azure demo.
- **Related records:** Q-004 answered; candidate FR-OP-12 and DEC-018 recorded as confirmed but not approved. Q-005 later clarified the database environment arrangement. See [open-questions.md](open-questions.md).

## Gate 2 — Local and hosted database arrangement

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Does “local SQL database” mean local SQL Server for development with Azure SQL for hosted environments, or is another environment arrangement intended?
- **Response:** “Azure SQL for local development and hosted environments.”
- **Recorded finding:** Azure SQL is the selected database service for both local-development and hosted environments. This does not imply that both environments use the same database instance or establish detailed connection/configuration practices.
- **Related records:** Q-005 answered; candidate FR-OP-13 and DEC-019 recorded as confirmed but not approved. Identity persistence in Azure SQL is reflected in FR-CA-14 and DEC-009. See [open-questions.md](open-questions.md).

## Gate 2 — Internal support staff enrollment

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** How should internal support staff accounts be enrolled?
- **Response:** “Tenant Admin invitation.”
- **Recorded finding:** Tenant Admin invites/provisions internal support staff accounts. This confirms who initiates enrollment, but not the detailed invitation, verification, or approval workflow.
- **Related records:** Q-006 partially answered; FR-OP-09 and DEC-013 clarified as confirmed but not approved. Authentication claims remain open and token lifetime/refresh-token details remain deferred to design. See [open-questions.md](open-questions.md).

## Gate 2 — JWT identity and authorization claims

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Which identity and authorization claims should authenticated user tokens carry?
- **Response:** “JWT should include UserId, UserName, TenantId, Role, and token expiry (`exp`). Additional permissions or claims can be finalized during detailed design. TenantId and roles must be validated server-side for authorization.”
- **Recorded finding:** JWTs must include UserId, UserName, TenantId, Role, and `exp`. TenantId and Role are validated server-side for authorization. Additional permissions or claims may be finalized during detailed design.
- **Related records:** Q-006 partially answered; candidate FR-OP-14 and DEC-020 recorded as confirmed but not approved. Token lifetime and refresh-token choice remain deferred under Q-026/Q-027. See [open-questions.md](open-questions.md).

## Gate 2 — Answer-generation model provider

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Which provider should supply the first-release assistant's answer-generation model?
- **Response:** “Azure AI Foundry.”
- **Recorded finding:** Azure AI Foundry is the selected provider for answer generation and embeddings. Exact model and region selection are deferred to detailed design; deployment configuration and cost envelope remain open.
- **Related records:** Q-007 partially answered; AI-004 and DEC-021 recorded as confirmed but not approved. See [open-questions.md](open-questions.md).

## Gate 2 — Answer-generation model selection

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Which specific Azure AI Foundry model should provide answer generation, or should that model choice be deferred to detailed design?
- **Response:** “Defer to detailed design.”
- **Recorded finding:** Exact answer-generation model selection is deferred to detailed design.
- **Related records:** Q-007 partially answered; the Azure AI Foundry provider choice remains confirmed, while model selection is deferred. See [open-questions.md](open-questions.md).

## Gate 2 — Embedding provider

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Which provider should supply the knowledge-base embedding model, or should that choice be deferred to detailed design?
- **Response:** “Azure AI Foundry.”
- **Recorded finding:** Azure AI Foundry is the selected provider for embeddings. Exact embedding model selection is deferred to detailed design.
- **Related records:** Q-007 partially answered; AI-004 and DEC-021 updated as confirmed but not approved. See [open-questions.md](open-questions.md).

## Gate 2 — Embedding model selection

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Should the specific embedding model be selected now or deferred to detailed design?
- **Response:** “Defer to detailed design.”
- **Recorded finding:** Exact embedding model selection is deferred to detailed design.
- **Related records:** Q-007 partially answered; Azure AI Foundry remains the selected embedding provider. See [open-questions.md](open-questions.md).

## Gate 2 — AI deployment region

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Which Azure region should host these deployments, or should the region be selected during detailed design?
- **Response:** “Defer to detailed design.”
- **Recorded finding:** Azure region selection for the Azure AI Foundry model and embedding deployments is deferred to detailed design.
- **Related records:** Q-007 partially answered; AI-004 and DEC-021 updated as confirmed but not approved. See [open-questions.md](open-questions.md).

## Gate 2 — AI cost envelope

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Is there an AI-specific cost ceiling for the demo, or should the cost envelope be addressed during detailed design?
- **Response:** “Defer to detailed design.”
- **Recorded finding:** AI model and embedding cost-envelope decisions are deferred to detailed design.
- **Related records:** Q-007 partially answered; the overall demo cost target remains open under Q-012. See [open-questions.md](open-questions.md).

## Gate 2 — Role/permission discovery scope

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Should the remaining role/permission matrix be specified during discovery, or deferred to detailed design?
- **Response:** “Specify now.”
- **Recorded finding:** The owner wants remaining role/permission boundaries specified during requirements discovery. This does not itself define any individual permission.
- **Related records:** Q-008 follow-ups clarified first-release role boundaries; detailed invitation/approval workflows remain deferred to design. See [open-questions.md](open-questions.md).

## Gate 2 — Non-knowledge role/permission discovery scope

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** For role permissions outside the first-release Knowledge Management/RAG scope, should any be specified now or deferred to detailed design/later phases?
- **Response:** “Specify now.”
- **Recorded finding:** The owner wants non-knowledge role/permission boundaries relevant to the first release specified during discovery, despite ticket capabilities being deferred. This does not itself define any permission.
- **Related records:** Q-008 follow-ups clarified applicable first-release permission boundaries one question at a time. See [open-questions.md](open-questions.md).

## Gate 2 — Tenant Admin knowledge access

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Should Tenant Admins be able to read tenant knowledge content, beyond their confirmed responsibility for managing knowledge sources and tenant users?
- **Response:** “Read and manage.”
- **Recorded finding:** Tenant Admins may read and manage knowledge content within their own tenant. A later clarification specified that this access covers all lifecycle statuses and preserved Support Manager or explicitly authorized higher-level role authority for external article review, approval, rejection, and publication.
- **Related records:** Q-008 was subsequently answered for first-release discovery; candidate FR-KB-13 and RULE-021 recorded as confirmed but not approved. See the following Q-008 clarification and [open-questions.md](open-questions.md).

## Gate 2 — Tenant Admin external article authority

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Should Tenant Admins be able to review/approve/reject/publish external articles, or should those actions remain with Support Managers and explicitly authorized higher-level roles?
- **Response:** “Support Manager authority.”
- **Recorded finding:** Tenant Admin read/manage access to tenant knowledge does not itself grant external article review, approval, rejection, or publication authority. Those actions remain with Support Managers or explicitly authorized higher-level roles.
- **Related records:** Q-008 clarified; RULE-021 and DEC-023 updated. Q-009 and Q-028 establish the related approval authority and role responsibilities. See [open-questions.md](open-questions.md).

## Gate 2 — Tenant Admin knowledge lifecycle scope

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Should Tenant Admin read/manage access cover all knowledge lifecycle statuses, or only a subset?
- **Response:** “All statuses.”
- **Recorded finding:** Tenant Admin read/manage access covers all tenant knowledge statuses, including draft, pending review, approved, rejected, and published.
- **Related records:** Q-008 clarified; FR-KB-13, RULE-021, ROLE-001, and DEC-023 updated as confirmed but not approved. See [open-questions.md](open-questions.md).

## Gate 2 — Support Agent internal knowledge status scope

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** For internal knowledge, may Support Agents access all lifecycle statuses, or only a subset?
- **Response:** “All statuses.”
- **Recorded finding:** Support Agents may retrieve internal knowledge in all lifecycle statuses. Q-008 follow-ups later confirmed all-tenant internal content management and external article authoring for Support Manager review, without approval or publication authority. The published-only restriction for external retrieval remains unchanged.
- **Related records:** Q-008 and Q-021 clarified; FR-CA-13, RULE-012, ROLE-002, and DEC-006 updated as confirmed but not approved. See [open-questions.md](open-questions.md).

## Gate 2 — Support Agent internal knowledge management

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** For internal knowledge management, may Support Agents edit/manage any internal knowledge in their tenant, or only content they uploaded/own?
- **Response:** “All internal.”
- **Recorded finding:** Support Agents may create, read, and manage any internal knowledge in their own tenant, independent of uploader. Their access to internal knowledge in all lifecycle statuses is unchanged.
- **Related records:** Q-008 and Q-021 clarified; FR-KB-14 and RULE-022 recorded as confirmed but not approved. External article authoring is clarified under FR-KB-15/RULE-023. See [open-questions.md](open-questions.md).

## Gate 2 — Support Agent external article authoring

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** May Support Agents create or edit external knowledge articles for Support Manager review, or should external-article management be limited to Tenant Admins/Support Managers?
- **Response:** “Create/edit articles for Support Manager review; no approval or publication.”
- **Recorded finding:** Support Agents may create and edit external articles for Support Manager review but may not approve, reject, or publish them.
- **Related records:** Q-008 clarified; FR-KB-15 and RULE-023 recorded as confirmed but not approved. See [open-questions.md](open-questions.md).

## Gate 2 — Tenant Admin external article authoring

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Should Tenant Admins also create/edit external articles for Support Manager review, or is their external-article management limited to reading/managing existing content?
- **Response:** “Create/edit articles for Support Manager review.”
- **Recorded finding:** Tenant Admins may create and edit external articles for Support Manager review but may not approve, reject, or publish them.
- **Related records:** Q-008 clarified; FR-KB-16 and RULE-021 recorded as confirmed but not approved. See [open-questions.md](open-questions.md).

## Gate 2 — Escalated customer conversation handling

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** For first-release escalations from external customers, which internal role(s) should be able to view the escalated conversation and respond?
- **Response:** “Support Agents.”
- **Recorded finding:** Support Agents may view and respond to external customer conversations escalated to human support.
- **Related records:** Q-008 clarified; candidate FR-CA-16, ROLE-002, and DEC-027 recorded as confirmed but not approved. See [open-questions.md](open-questions.md).

## Gate 2 — Remaining permission scope

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Are there any additional first-release role/permission boundaries to specify now, or should remaining non-knowledge permissions be deferred with the out-of-scope capabilities?
- **Response:** “No additional; defer non-knowledge permissions for out-of-scope capabilities.”
- **Recorded finding:** No further first-release role/permission boundaries were requested. Remaining non-knowledge permissions are deferred with the related out-of-scope capabilities; detailed invitation/approval workflow remains deferred to design.
- **Related records:** Q-008 answered for first-release role/permission scope; non-knowledge capabilities remain deferred. See [open-questions.md](open-questions.md).

## Gate 2 — Document retention start and deletion scope

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** When should the baseline's 90-day document-retention period begin, and which original or derived copies should be deleted or retained?
- **Response:** “The 90-day retention period should start from the original document upload date. After expiry, the source document and associated extracted text, chunks, and embeddings should be deleted. Backup deletion, log retention, and evaluation-record retention policies remain open for detailed design and compliance review.”
- **Recorded finding:** The 90-day period starts on original upload; the source document, extracted text, chunks, and embeddings must be deleted after expiry. Backup deletion and log/evaluation-record retention remain unresolved for detailed design and compliance review. This period remains distinct from the 90-day knowledge-review interval.
- **Related records:** Q-010 partially answered; DATA-002 and DEC-028 updated. No complete requirements approval is implied. See [open-questions.md](open-questions.md).

## Gate 2 — AI/RAG evaluation criteria

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** What evaluation results or thresholds, if any, should be required for first release across retrieval, grounding, citation correctness, abstention, and prompt-injection handling?
- **Response:** “Keep all first-release AI/RAG evaluation thresholds open for now, including retrieval quality, answer grounding, citation correctness, abstention, and prompt-injection handling. Define measurable metrics, evaluation datasets, and acceptance thresholds during AI/RAG detailed design before release approval.”
- **Recorded finding:** No specific first-release AI/RAG metrics or thresholds are set during discovery. Measurable metrics, evaluation datasets, and acceptance thresholds must be defined during AI/RAG detailed design before release approval.
- **Related records:** Q-011 partially answered; AI-002 and DEC-029 updated. No complete requirements approval is implied. See [open-questions.md](open-questions.md).

## Gate 2 — Demo operating targets

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Are there required numeric targets for latency, availability/recovery, concurrency, or total cost for the demo?
- **Response:** “No confirmed numeric targets yet. Keep latency, availability/recovery, concurrency, and operating cost open for now. Define measurable targets during detailed design and performance testing before release approval.”
- **Recorded finding:** No numeric targets are confirmed for latency, availability/recovery, concurrency, or operating cost. Measurable targets must be defined during detailed design and performance testing before release approval.
- **Related records:** Q-012 partially answered; DEC-030 and related risk/requirement notes updated. No complete requirements approval is implied. See [open-questions.md](open-questions.md).

## Gate 2 — Synthetic ticket data scope

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Since ticket AI and analytics are deferred from the first-release scope, should synthetic ticket taxonomy, fields, and seed strategy also be deferred, or specified now for demonstration/testing?
- **Response:** “Defer synthetic ticket taxonomy, fields, and seed data strategy until ticket AI and analytics are included in a future phase. Keep the first release focused on knowledge management and the RAG-based assistant.”
- **Recorded finding:** Defer synthetic ticket taxonomy, fields, and seed strategy until ticket AI and analytics enter a future phase; the first release remains focused on knowledge management and the RAG assistant.
- **Related records:** Q-013 answered for current release scope; DEC-031 and DEP-004 updated. No complete requirements approval is implied. See [open-questions.md](open-questions.md).

## Gate 2 — Accessibility and language scope

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** What user-facing accessibility and language scope is required for the first release?
- **Response:** “First release should support English only. Accessibility conformance level (WCAG) remains undecided and will be finalized during detailed design. Follow basic accessibility practices, including keyboard navigation, readable contrast, labels, and screen-reader-friendly controls.”
- **Recorded finding:** First-release language scope is English only. Basic accessibility practices include keyboard navigation, readable contrast, labels, and screen-reader-friendly controls. WCAG conformance level remains open for detailed design.
- **Related records:** Q-014 partially answered; NFR-007 and DEC-032 updated. No complete requirements approval is implied. See [open-questions.md](open-questions.md).

## Gate 2 — Issue, PR, CI, and delivery workflow scope

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Which GitHub issue/PR, CI, and delivery workflow requirements are essential for the first release?
- **Response:** “Next phase we will take this.”
- **Recorded finding:** The owner deferred specifying GitHub issue/PR, CI, and delivery workflow requirements to the next phase. No first-release workflow scope was specified.
- **Related records:** Q-018 answered for current discovery; DEC-033 and DEP-006 updated. No complete requirements approval is implied. See [open-questions.md](open-questions.md).

## Gate 2 — API contract scope

- **Stakeholder:** Project owner
- **Date:** 2026-11-12 (session date)
- **Question:** Should illustrative API contract details be deferred to solution/detailed design, or are there specific API behaviors that must be fixed in requirements now?
- **Response:** “Defer detailed API schemas, endpoint paths, validation rules, pagination, idempotency, and error-response formats to solution/detailed design. Requirements must confirm authentication, tenant isolation, role-based authorization, secure access to knowledge, and consistent document deletion across source and derived data.”
- **Recorded finding:** Detailed API schemas, paths, validation, pagination, idempotency, and error formats are deferred. Requirements must preserve authentication, tenant isolation, role-based authorization, secure knowledge access, and consistent deletion across source and derived data.
- **Related records:** Q-019 partially answered; API-001 and DEC-034 updated. No complete requirements approval is implied. See [open-questions.md](open-questions.md).

## Gate 2 — Discovery findings review

- **Stakeholder:** Project owner
- **Date:** Not recorded
- **Review:** Gate 2 discovery findings and unresolved/deferred items.
- **Response:** Approved the Gate 2 findings and authorized preparation of the requirements package for Gate 3 review.
- **Recorded finding:** Gate 2 is approved. This does not approve the complete requirements or individual requirements and does not authorize PRD finalization or implementation planning.
- **Related records:** DEC-035 and EV-061. Gate 3 approval was pending at this review and was subsequently recorded under DEC-036 and EV-062.

## Gate 3 — Requirements approval

- **Stakeholder:** Project owner
- **Date:** Not recorded
- **Review:** Gate 3 requirements package, including business/functional/non-functional requirements, business rules, scope, priorities, traceability, candidate stories and acceptance criteria, and unresolved/deferred items.
- **Response:** Approved the requirements package as presented.
- **Recorded finding:** Gate 3 requirements approval was recorded for the package as presented. Items explicitly retained as Draft/unprioritized and unresolved or deferred decisions retain those statuses. At that point, Gate 4 PRD approval and Gate 5 implementation-planning authorization remained pending; Gate 4 was subsequently approved under DEC-037 and EV-063.
- **Related records:** DEC-036 and EV-062.

## Gate 4 — PRD approval

- **Stakeholder:** Project owner
- **Date:** Not recorded
- **Review:** [SupportIQ Product Requirements Document](../approved/PRD.md)
- **Response:** Approved the PRD, with Q-033 (the baseline's 10 MB per-file upload maximum) remaining open and documented.
- **Recorded finding:** Gate 4 PRD approval is recorded. Q-033 remained open at the time and was not resolved by that approval; it was subsequently resolved under DEC-040. At that time, implementation planning remained unauthorized; separate Gate 5 authorization was subsequently recorded under DEC-038.
- **Related records:** DEC-037 and EV-063.

## Gate 5 — Implementation-planning authorization

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Review:** Gate 5 authorization prompt for the selected implementation-planning workflow.
- **Response:** Yes; authorized preparation of an implementation-planning draft.
- **Recorded finding:** Gate 5 planning authorization is recorded. At that point it did not approve the resulting plan or authorize implementation; the plan was subsequently approved under DEC-039. Q-033 (the baseline's 10 MB per-file upload maximum) was open at the time and was subsequently resolved under DEC-040.
- **Related records:** DEC-038 and EV-064.

## Implementation plan approval

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Review:** [SupportIQ Implementation Plan](../../implementation/implementation-plan.md) and [Feature and Task Board](../../implementation/feature-task-board.md).
- **Response:** Approved the implementation plan as written.
- **Recorded finding:** The planning artifact is approved. This approval does not authorize implementation or resolve the open requirements/design decisions that remained at that time; Q-033 was subsequently resolved under DEC-040.
- **Related records:** DEC-039 and EV-065.

## Q-033 — Per-file upload maximum

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Does the baseline's 10 MB maximum per uploaded file remain the approved first-release limit?
- **Response:** “we can mark 10MB upload file limit”
- **Recorded finding:** Confirmed a maximum upload size of 10 MB per file for the first release. Q-033 is resolved; the original baseline remains unchanged.
- **Related records:** DEC-040, EV-066, FR-KB-17, AC-014, and CHG-001.

## Q-034 — Upload limit byte interpretation

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Does the 10 MB per-file maximum mean 10,000,000 bytes (decimal MB) or 10,485,760 bytes (10 MiB)?
- **Response:** “10,000,000 bytes (decimal MB)”
- **Recorded finding:** Enforce a maximum of 10,000,000 bytes per uploaded file. Q-034 is resolved; this clarifies implementation of the approved 10 MB limit and does not change it.
- **Related records:** DEC-055, EV-081, FR-KB-17, and AC-014.

## Implementation authorization and technology stack

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Review:** Current implementation progress and the proposed application stack.
- **Response:** “we can start it”; approved the proposed stack.
- **Recorded finding:** Implementation is authorized to begin. The approved stack is .NET 10 / ASP.NET Core, React with TypeScript, Bootstrap, SQL Server, local database identity with JWT, and Azure AI Foundry. Exact architecture boundaries and remaining service/configuration choices are not resolved by this approval.
- **Related records:** DEC-041, DEC-042, EV-067, and EV-068.

## Frontend tooling approval

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Review:** Selection of the React + TypeScript development/build tool.
- **Response:** Approved Vite.
- **Recorded finding:** Vite is approved as frontend development/build tooling; this does not change the approved application stack.
- **Related records:** DEC-043 and EV-069.

## Backend architecture decision

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** For the first release, should the backend use a modular monolith (one ASP.NET Core API organized by feature, with the React app separate) or independently deployed microservices?
- **Response:** “Modular monolith.”
- **Recorded finding:** Use one ASP.NET Core API deployment organized into feature-oriented modules, with the React frontend as a separate application. Search, file storage, background processing, and other service decisions remain open.
- **Related records:** DEC-044, EV-070, and [ADR-001](../../architecture/decisions/ADR-001-modular-monolith.md).

## Knowledge search/index decision

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Should SupportIQ use Azure AI Search for keyword and vector retrieval, or defer the search provider decision?
- **Response:** Approved Azure AI Search.
- **Recorded finding:** Azure AI Search is the approved search/index service for knowledge retrieval. Resource provisioning, index configuration, embedding-model compatibility, and cost decisions remain open.
- **Related records:** DEC-045, EV-071, and [ADR-002](../../architecture/decisions/ADR-002-azure-ai-search.md).

## Source-document storage decision

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Should source documents use Azure Blob Storage in both local and hosted environments, or use a local filesystem during development and Blob Storage when hosted?
- **Response:** “Blob in both environments.”
- **Recorded finding:** Use Azure Blob Storage for source documents in local development and hosted Azure. The local connection method (emulator or Azure development resource) and resource configuration are not yet selected; no resources are provisioned by this decision.
- **Related records:** DEC-046, EV-072, and [ADR-003](../../architecture/decisions/ADR-003-azure-blob-storage.md).

## Local Blob Storage connection decision

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Should local development use an Azurite emulator or connect to an Azure development storage account?
- **Response:** “Azure dev storage.”
- **Recorded finding:** Local development is intended to connect to an Azure development storage account. Account availability and configuration remain unverified; inspection was declined and provisioning was not authorized.
- **Related records:** DEC-047, EV-073, and [ADR-003](../../architecture/decisions/ADR-003-azure-blob-storage.md).

## Background document-processing decision

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Which asynchronous document-processing approach should be used: an API-hosted SQL job queue or a separate Azure Function triggered by a queue?
- **Response:** “azure function triggered by azure service bus queue”
- **Recorded finding:** Use an Azure Function triggered by an Azure Service Bus queue for asynchronous document processing. Function/namespace/queue configuration, local connection, retry and idempotency behavior, and resource provisioning remain open.
- **Related records:** DEC-048, EV-074, and [ADR-004](../../architecture/decisions/ADR-004-azure-function-service-bus-processing.md).

## Local Service Bus connection decision

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Should the locally running Azure Function connect to a dedicated Azure development Service Bus namespace, or should the local queue connection be deferred?
- **Response:** “Dedicated Azure dev namespace.”
- **Recorded finding:** Local Function execution will use a dedicated Azure development Service Bus namespace. Namespace availability and configuration remain unverified; credentials must not be committed, and no resources are provisioned by this decision.
- **Related records:** DEC-049, EV-075, and [ADR-004](../../architecture/decisions/ADR-004-azure-function-service-bus-processing.md).

## SQL data-access decision

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Should application persistence use Entity Framework Core or Dapper/custom SQL with SQL Server/Azure SQL?
- **Response:** Approved EF Core.
- **Recorded finding:** Use Entity Framework Core with SQL Server/Azure SQL. Entity/schema design and database contracts remain subject to approved requirements and detailed design.
- **Related records:** DEC-050, EV-076, and [ADR-005](../../architecture/decisions/ADR-005-ef-core.md).

## First-release token-renewal decision

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Should the first release issue refresh tokens or require reauthentication after a configurable-expiry JWT access token expires?
- **Response:** “No refresh tokens initially.”
- **Recorded finding:** Do not issue refresh tokens in the first release; users renew access by authenticating again. Access-token lifetime remains configurable and its value is undecided.
- **Related records:** DEC-051, EV-077, Q-027, and [ADR-006](../../architecture/decisions/ADR-006-jwt-session-lifecycle.md).

## JWT revocation decision

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Should JWT revocation use a per-token SQL denylist or user-wide ASP.NET Core Identity security-stamp validation?
- **Response:** “User-wide security stamp.”
- **Recorded finding:** Revoke all active JWTs for a user by changing the user's Identity security stamp and validating the token stamp against the current user stamp on authenticated requests.
- **Related records:** DEC-052, EV-078, `FR-OP-11`, and [ADR-006](../../architecture/decisions/ADR-006-jwt-session-lifecycle.md).

## Internal tenant-membership cardinality

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Can an internal support user have active membership in multiple tenants, or only one?
- **Response:** “Single tenant.”
- **Recorded finding:** An internal support user may have active membership in one tenant only. The API derives tenant scope and role from active membership, never from a caller-selected tenant parameter or header.
- **Related records:** DEC-053, EV-079, and [ADR-007](../../architecture/decisions/ADR-007-single-tenant-membership.md).

## Sign-in identifier decision

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Should users authenticate with username, email address, or either?
- **Response:** “Email.”
- **Recorded finding:** Use email address and password for sign-in for internal and external accounts. Keep the approved user-name JWT claim; registration, verification, invitation, and password-reset workflows remain deferred.
- **Related records:** DEC-054, EV-080, and the [API contract draft](../api-contracts.md).

## Initial API contract review — token route

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Is `POST /api/v1/auth/token` acceptable as the first-release email/password token-issuance route?
- **Response:** “Keep POST /api/v1/auth/token”
- **Recorded finding:** The owner approved this route. Request/response schema details and the remaining endpoint paths and payloads remain draft.
- **Related records:** DEC-056, EV-082, `FR-OP-10`, `FR-CA-14`, and [API contract draft](../api-contracts.md).

## Initial API contract review — token response

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Should the token response include the proposed user identity object (`userId`, `userName`, `tenantId`, `roles`) alongside the token fields?
- **Response:** “Include the user object”
- **Recorded finding:** The owner approved the proposed response shape, including the user identity object and token metadata. Remaining request/response details stay draft.
- **Related records:** DEC-057, EV-083, `FR-OP-10`, `FR-CA-14`, and [API contract draft](../api-contracts.md).

## Initial API contract review — token request fields

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Should the token request use `email` and `password` as its JSON property names?
- **Response:** “Keep email and password”
- **Recorded finding:** The owner approved `email` and `password` as request property names. Credential validation/error behavior and remaining contract details stay draft.
- **Related records:** DEC-058, EV-084, `FR-OP-10`, `FR-CA-14`, and [API contract draft](../api-contracts.md).

## Initial API contract review — invalid credentials

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** Should invalid email and password combinations return the same generic authentication error?
- **Response:** “Same generic error”
- **Recorded finding:** Return the same generic authentication error for an unknown email and an incorrect password, without revealing whether an account exists.
- **Related records:** DEC-059, EV-085, `FR-OP-10`, `FR-CA-14`, and [API contract draft](../api-contracts.md).

## Platform Admin JWT tenant-claim amendment

- **Stakeholder:** Project owner
- **Date:** 2026-11-12
- **Question:** How should the Platform Admin JWT represent `TenantId`, given the Gate 3-approved requirement that tokens include the claim and the Platform Admin boundary that prohibits tenant-content access?
- **Response:** “Omit TenantId for Platform Admin”
- **Explicit requirement-change approval:** Approved changing FR-OP-14 so tenant-scoped users include `TenantId` and Platform Admin tokens omit it.
- **Recorded finding:** Platform Admin JWTs omit `TenantId`; tenant-scoped identities retain it. `UserId`, `UserName`, `Role`, and `exp` remain required. This is an approved post-Gate-3 amendment; the original baseline is unchanged.
- **Related records:** DEC-020 (amended), DEC-060, EV-086, CHG-004, FR-OP-14, and [API contract draft](../api-contracts.md).
