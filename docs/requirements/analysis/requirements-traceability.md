# SupportIQ Requirements Traceability

## Status

Gate 3-approved requirements traceability. The project owner approved the requirements package, including these user stories, acceptance criteria, and mappings, as presented. Remaining baseline-only Draft/unprioritized items and unresolved or deferred decisions retain their statuses. Source requirements and status are recorded in [requirements-inventory.md](requirements-inventory.md); the original baseline remains unchanged.

## User stories

| ID | Approved user story | Source and status |
|---|---|---|
| US-001 | As a Support Agent, I want to create, read, and manage internal knowledge in my tenant, regardless of uploader, and retrieve it across lifecycle statuses, so that I can support customers with relevant information. | `FR-KB-14`, `FR-CA-13`, `RULE-022`; Approved at Gate 3 |
| US-002 | As a Tenant Admin, I want to manage tenant membership and knowledge content and create/edit external articles for Support Manager review, so that tenant operations remain within my authority. | `FR-OP-09`, `FR-KB-13`, `FR-KB-16`, `RULE-013`, `RULE-021`, `RULE-024`; Approved at Gate 3 |
| US-003 | As a Support Agent, I want to create/edit external articles for Support Manager review without approving or publishing them, so that external content retains its required approval boundary. | `FR-KB-15`, `RULE-023`; Approved at Gate 3 |
| US-004 | As a Support Manager, I want to review, approve, reject, publish, and manage restrictions for external knowledge, so that only authorized content is available to external customers. | `FR-KB-09`, `FR-CA-13`, `RULE-009`, `RULE-012`, `RULE-016`; Approved at Gate 3 |
| US-005 | As an external customer, I want answers from approved and published knowledge and access only to my own conversation history, so that other tenants' or users' information is not exposed. | `FR-CA-10`, `FR-CA-11`, `FR-CA-15`, `RULE-014`, `RULE-015`; Approved at Gate 3 |
| US-006 | As a Support Agent, I want to view and respond to customer conversations escalated to human support, so that unanswered questions can receive human assistance. | `FR-CA-12`, `FR-CA-16`; Approved at Gate 3 |
| US-007 | As a Platform Admin, I want to inspect permitted platform-level operational metadata without accessing tenant business content, so that platform operations do not cross the tenant-content boundary. | `ROLE-004`, `RULE-010`, `RULE-011`; Approved at Gate 3 |

These stories were approved as part of the Gate 3 package and do not add capabilities beyond the recorded sources and stakeholder responses.

## Acceptance criteria

| ID | Approved acceptance criterion | Trace | Status / limits |
|---|---|---|---|
| AC-001 | An external-customer assistant request can retrieve only knowledge that is explicitly approved and published, meets the recorded external-content criteria, and belongs to the customer's authorized tenant scope. | `US-005`; `FR-CA-10`, `FR-CA-11`, `FR-KB-09`; `RULE-009`, `RULE-017` | Approved at Gate 3 |
| AC-002 | A Support Agent can retrieve internal knowledge in all lifecycle statuses within the agent's own tenant. Published external knowledge is available by default within that tenant unless a Support Manager-configured role/permission restriction applies. | `US-001`; `FR-CA-13`, `FR-KB-14`; `RULE-012`, `RULE-022` | Approved at Gate 3; detailed restriction assignment remains deferred |
| AC-003 | Tenant Admins and Support Agents can create/edit external articles for Support Manager review but cannot approve, reject, or publish them. Only a Support Manager or explicitly authorized higher-level role can perform external approval/publication actions. | `US-002`, `US-003`, `US-004`; `FR-KB-09`, `FR-KB-13`, `FR-KB-15`, `FR-KB-16`; `RULE-009`, `RULE-021`, `RULE-023`, `RULE-024` | Approved at Gate 3 |
| AC-004 | An external customer can access only conversation history created under that customer's authenticated account and associated tenant; requests for another customer's or internal staff's conversation history are denied. | `US-005`; `FR-CA-15`; `RULE-014`, `RULE-015` | Approved at Gate 3; history retention/deletion remains deferred |
| AC-005 | A customer conversation escalated to human support can be viewed and answered by a Support Agent without broadening the external customer's access to other conversation history. | `US-005`, `US-006`; `FR-CA-12`, `FR-CA-16` | Approved at Gate 3 |
| AC-006 | Tenant membership actions are performed by the Tenant Admin or an explicitly authorized higher-level role; data access is limited to active tenant membership; membership changes are audit-logged. | `US-002`; `FR-OP-09`; `RULE-013` | Approved at Gate 3; invitation/approval workflow details remain deferred |
| AC-007 | A Platform Admin can access the specified platform-level metadata, but cannot access tenant-specific business content, customer data, tickets, knowledge articles, or uploaded documents. | `US-007`; `ROLE-004`; `RULE-010`, `RULE-011` | Approved at Gate 3 |
| AC-008 | An outdated external article is flagged for review and withdrawn from external access until updated and reapproved; the configured review process supports the recorded triggers, a 90-day default interval, and per-article review-date overrides. | `US-004`; `FR-KB-10`–`FR-KB-12`; `RULE-018`–`RULE-020` | Approved at Gate 3 |
| AC-009 | Ninety days after original upload, the source document, extracted text, chunks, and embeddings are deleted. | `DATA-002`, `DEC-028`, `Q-010` | Approved at Gate 3; backup deletion and log/evaluation-record retention remain open |
| AC-010 | Authenticated API access enforces server-derived tenant isolation, role-based authorization, secure knowledge access, and consistent deletion across source and derived document data. | `API-001`, `FR-CA-14`, `FR-OP-09`, `DATA-002`, `DEC-034` | Approved at Gate 3; endpoint paths, schemas, validation details, pagination, idempotency, and error formats are deferred |
| AC-011 | The first release supports English and applies keyboard navigation, readable contrast, labels, and screen-reader-friendly controls. | `NFR-007`, `NFR-011`, `DEC-032` | Approved at Gate 3; WCAG conformance level remains open |
| AC-012 | AI/RAG detailed design documents evaluation datasets, measurable metrics, and acceptance thresholds for retrieval quality, grounding, citation correctness, abstention, and prompt-injection handling before release approval. | `AI-002`, `Q-011`, `DEC-029` | Approved at Gate 3 as a release-readiness condition; specific metrics and thresholds remain deferred |
| AC-013 | Before release approval, measurable latency, availability/recovery, concurrency, and operating-cost targets are defined and performance testing is conducted against the approved targets. | `Q-012`, `DEC-030`, `NFR-004`, `NFR-008`, `NFR-009` | Approved at Gate 3 as a release-readiness condition; no target values are set |

## Business-to-system traceability

| Business requirement | Related system requirements | Approved story / acceptance criteria | Test cases |
|---|---|---|---|
| BR-001 | `FR-OP-*`, `NFR-*`, `DATA-003`, `ROLE-*` | US-001–US-007; AC-006, AC-007, AC-011 | No test-case IDs assigned |
| BR-002 | First-release `FR-CA-*`, `FR-KB-*`, `AI-001`, `AI-003`, `RULE-*` | US-001–US-006; AC-001–AC-008 | No test-case IDs assigned |
| BR-003 | `FR-EV-*`, `FR-OP-*`, `NFR-001`, `AI-002` | AC-010, AC-012 | No test-case IDs assigned; metrics and thresholds are deferred to detailed design |
| BR-004 | `FR-OP-04`–`FR-OP-08`, `NFR-003`–`NFR-010`, `API-001` | AC-010, AC-013 | No test-case IDs assigned; CI/delivery workflow requirements are deferred to the next phase |
| BR-005 | Later-pilot measurement; no baseline metric or target | No candidate story or acceptance criterion defined | Deferred until a pilot and its measures are authorized |

## Traceability limitations

- Stories and acceptance criteria were approved as part of the Gate 3 package. Test-case IDs and executable test designs were not included and remain for later test planning.
- Baseline acceptance statements for ticket AI, analytics, CI, and additional tools remain source evidence; corresponding capabilities are not promoted into first-release scope where the owner deferred them.
- The PRD was approved at Gate 4 with Q-033 remaining open; implementation planning has not been authorized.
