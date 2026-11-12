# Implementation Progress Log

Append new entries. Do not erase previous entries.

## 2026-11-12 — Implementation authorized

- Plan version: 0.3
- Branch/commit: working tree based on `0c081a7`
- Summary: Project owner authorized implementation, approved the proposed stack, and approved Vite as React frontend tooling.
- Work items changed: TASK-045 solution scaffold completed under `src\backend` and `src\frontend`; TASK-001 remains in progress while detailed architecture/service decisions are unresolved.
- Tests/CI: `dotnet build SupportIQ.sln` passed with zero warnings/errors; frontend `npm run build` and `npm run lint` passed; API `/health` returned HTTP 200 with `{"status":"ok"}`. npm reported zero vulnerabilities.
- Blockers: Search, file-storage, background-processing, Foundry deployment, and detailed API/data/identity choices remain open.
- Decisions required: Resolve TASK-002 and TASK-003 before dependent feature implementation or Azure provisioning.
- Scope changes: No product requirements changed; TASK-045 records a missing implementation foundation deliverable.
- Next recommended action: Complete detailed API/data/identity and Azure service decisions under TASK-001–TASK-003 before starting dependent feature implementation.

## 2026-11-12 — Backend architecture selected

- Plan version: 0.4
- Branch/commit: working tree based on `0c081a7`
- Summary: Project owner selected a modular monolith: one feature-oriented ASP.NET Core API deployment with the React frontend as a separate application.
- Work items changed: TASK-001 remains in progress; architecture decision recorded as DEC-044 / EV-070 and ADR-001.
- Tests/CI: Documentation-only decision update; no additional build needed.
- Blockers: Persistence contract, search, file storage, background processing, Foundry deployment/configuration, and local/hosted resource details remain open.
- Decisions required: Continue TASK-001/003 service decisions and then define TASK-002 contracts.
- Scope changes: No product requirements changed.
- Next recommended action: Resolve a service decision needed for ingestion and RAG before detailed contract implementation.

## 2026-11-12 — Knowledge search service selected

- Plan version: 0.5
- Branch/commit: working tree based on `0c081a7`
- Summary: Project owner approved Azure AI Search for knowledge keyword/vector retrieval.
- Work items changed: TASK-003 is in progress; decision recorded as DEC-045 / EV-071 and ADR-002.
- Tests/CI: Documentation-only decision update; no additional build needed.
- Blockers: File storage, background processing, Foundry model/deployment, search resource/index configuration, and local/hosted connectivity remain open.
- Decisions required: Decide file-storage approach next; do not provision Azure resources without approval.
- Scope changes: No product requirements changed.
- Next recommended action: Confirm the file-storage approach for source documents across local development and hosted demo.

## 2026-11-12 — Source-document storage selected

- Plan version: 1.1
- Branch/commit: working tree based on `0c081a7`
- Summary: Project owner selected Azure Blob Storage for source documents in both local and hosted environments.
- Work items changed: TASK-003 remains in progress; decision recorded as DEC-046 / EV-072 and ADR-003.
- Tests/CI: Documentation-only decision update; no additional build needed.
- Blockers: Local Azure storage account availability/configuration, background processing, Foundry model/deployment, resource configuration, and provisioning remain open.
- Decisions required: Azure development storage was selected for local connection, but account availability/configuration is unverified. Do not inspect or provision Azure resources without approval.
- Scope changes: No product requirements changed.
- Next recommended action: Define API/data/identity contracts and select an approved Foundry deployment; keep Azure account access/provisioning gated.

## 2026-11-12 — Authentication session behavior selected

- Plan version: 1.2
- Branch/commit: working tree based on `0c081a7`
- Summary: Project owner chose no refresh tokens in the first release and user-wide revocation through ASP.NET Core Identity security-stamp validation.
- Work items changed: TASK-001 is complete; TASK-002 is in progress. Decisions recorded as DEC-051/DEC-052 and EV-077/EV-078; Q-027 resolved. Exact access-token lifetime remains open under Q-026.
- Tests/CI: Documentation-only decision update; no additional build needed.
- Blockers: Tenant membership cardinality and remaining API/data contracts remain to be defined; no local Azure account access or resource provisioning is authorized.
- Decisions required: Clarify whether a user may have active membership in multiple tenants before finalizing tenant claims and request scope.
- Scope changes: No product requirements changed; renewal/revocation design follows FR-OP-11.
- Next recommended action: Clarify whether a user may have active membership in multiple tenants before finalizing tenant claims and request scope.

## 2026-11-12 — Internal membership cardinality selected

- Plan version: 1.2
- Branch/commit: working tree based on `0c081a7`
- Summary: Project owner confirmed internal support users have active membership in one tenant only.
- Work items changed: TASK-001 remains done; TASK-002 remains in progress. Decision recorded as DEC-053 / EV-079 and ADR-007.
- Tests/CI: Documentation-only decision update; no additional build needed.
- Blockers: Detailed API/data contracts remain in progress; local Azure account access and resource provisioning are not authorized.
- Decisions required: Continue API contract design; keep tenant/role scope server-derived and do not accept caller-selected tenant IDs.
- Scope changes: No product requirements changed.
- Next recommended action: Document the detailed API/data/auth contracts before implementing authenticated feature endpoints.

## 2026-11-12 — Email sign-in decision and API contract draft

- Plan version: 1.3
- Branch/commit: working tree based on `0c081a7`
- Summary: Project owner selected email/password sign-in under DEC-054. Draft API contracts were added for review; proposed endpoint paths and schemas are not approved public contracts.
- Work items changed: TASK-001 remains done; TASK-002 and TASK-003 remain in progress. Task board reconciled to plan version 1.3.
- Tests/CI: Documentation-only updates; `git diff --check` remains to be run.
- Blockers: Exact JWT lifetime, upload byte interpretation, final API/data contracts, Foundry deployment configuration, and Azure development-resource availability remain unresolved. No Azure resource access or provisioning is authorized.
- Decisions required: Clarify whether 10 MB means 10,000,000 bytes or 10,485,760 bytes; review the API contract draft before feature endpoint implementation.
- Scope changes: No product requirements changed.
- Next recommended action: Resolve Q-034 and continue review of the draft API/data/auth contracts.

## 2026-11-12 — Upload byte threshold confirmed

- Plan version: 1.3
- Branch/commit: working tree based on `0c081a7`
- Summary: Project owner clarified that the approved 10 MB maximum means 10,000,000 bytes (decimal MB), not 10 MiB.
- Work items changed: Q-034 resolved; DEC-055 / EV-081 recorded. Updated the PRD, change log, API contract draft, and feature/task board.
- Tests/CI: Documentation-only updates; `git diff --check` passed.
- Blockers: Detailed API/data/auth contracts remain in draft; exact JWT lifetime, Foundry deployment configuration, and Azure development-resource availability remain unresolved. Azure resource access and provisioning remain unauthorized.
- Decisions required: Review the draft API/data/auth contracts before implementing authenticated feature endpoints.
- Scope changes: No product requirements changed; this specifies the byte-level implementation of the approved 10 MB maximum.
- Next recommended action: Continue TASK-002 review of detailed API/data/auth contracts; preserve unresolved items as draft until approved.

## 2026-11-12 — Initial API contract review

- Plan version: 1.3
- Branch/commit: working tree based on `0c081a7`
- Summary: Project owner approved `POST /api/v1/auth/token` as the first-release email/password token-issuance route.
- Work items changed: DEC-056 / EV-082 recorded; the API contract draft marks this route approved. TASK-002 remains in progress.
- Tests/CI: Documentation-only updates; `git diff --check` remains to be run.
- Blockers: Request/response schema details and all other proposed routes/payloads remain unreviewed; exact JWT lifetime, Foundry deployment configuration, and Azure development-resource availability remain unresolved. Azure resource access and provisioning remain unauthorized.
- Decisions required: Continue reviewing the remaining authentication contract details and endpoint proposals one item at a time.
- Scope changes: No product requirements changed; one API route was approved.
- Next recommended action: Review the token issuance request/response contract, beginning with the email/password request fields and token response shape.

## 2026-11-12 — Token response shape reviewed

- Plan version: 1.3
- Branch/commit: working tree based on `0c081a7`
- Summary: Project owner approved including the proposed user identity object in the token-issuance response alongside token metadata.
- Work items changed: DEC-057 / EV-083 recorded; the token response shape is marked approved in the API contract draft. TASK-002 remains in progress.
- Tests/CI: Documentation-only updates; `git diff --check` remains to be run.
- Blockers: Request schema details and other endpoint paths/payloads remain unreviewed; exact JWT lifetime, Foundry deployment configuration, and Azure development-resource availability remain unresolved. Azure resource access and provisioning remain unauthorized.
- Decisions required: Continue reviewing the remaining authentication contract details and endpoint proposals one item at a time.
- Scope changes: No product requirements changed; one response shape was approved.
- Next recommended action: Review the token-issuance request body field names and validation behavior.

## 2026-11-12 — Token request field names reviewed

- Plan version: 1.3
- Branch/commit: working tree based on `0c081a7`
- Summary: Project owner approved `email` and `password` as the JSON properties for token issuance.
- Work items changed: DEC-058 / EV-084 recorded; request field names are marked approved in the API contract draft. TASK-002 remains in progress.
- Tests/CI: Documentation-only updates; `git diff --check` remains to be run.
- Blockers: Credential validation/error behavior and remaining endpoint contracts are unreviewed; exact JWT lifetime, Foundry deployment configuration, and Azure development-resource availability remain unresolved. Azure resource access and provisioning remain unauthorized.
- Decisions required: Continue reviewing authentication response/error behavior and the remaining endpoint proposals one item at a time.
- Scope changes: No product requirements changed; request property names were approved.
- Next recommended action: Review the proposed handling of failed sign-in credentials for account-enumeration resistance.

## 2026-11-12 — Invalid-credentials behavior reviewed

- Plan version: 1.3
- Branch/commit: working tree based on `0c081a7`
- Summary: Project owner approved returning the same generic authentication error for an unknown email and an incorrect password.
- Work items changed: DEC-059 / EV-085 recorded; failed-sign-in behavior is documented in the API contract draft. TASK-002 remains in progress.
- Tests/CI: Documentation-only updates; `git diff --check` remains to be run.
- Blockers: Remaining endpoint paths/payloads, error details, and non-authentication contracts remain unreviewed; exact JWT lifetime, Foundry deployment configuration, and Azure development-resource availability remain unresolved. Azure resource access and provisioning remain unauthorized.
- Decisions required: Continue reviewing the remaining authentication contract details and endpoint proposals one item at a time.
- Scope changes: No product requirements changed; failed-credential response behavior was approved.
- Next recommended action: Review which JWT claim names are included in the token, ensuring approved identity and tenant invariants are preserved.

## 2026-11-12 — Platform Admin tenant claim requirement amended

- Plan version: 1.4
- Branch/commit: working tree based on `0c081a7`
- Summary: Project owner explicitly approved changing the Gate 3 requirement so Platform Admin JWTs omit `TenantId`; tenant-scoped users retain it.
- Work items changed: FR-OP-14, PRD, implementation-plan acceptance criteria, API contract, and evidence records updated under DEC-060 / EV-086 / CHG-004. Plan and task board reconciled to version 1.4.
- Tests/CI: Documentation-only updates; `git diff --check` remains to be run.
- Blockers: Remaining endpoint paths/payloads, error details, and non-authentication contracts remain unreviewed; exact JWT lifetime, Foundry deployment configuration, and Azure development-resource availability remain unresolved. Azure resource access and provisioning remain unauthorized.
- Decisions required: Continue reviewing the remaining authentication contract details and endpoint proposals one item at a time.
- Scope changes: Approved requirement change; the original baseline remains unchanged.
- Next recommended action: Review the proposed JWT lifetime/configuration and confirm it remains unresolved until separately decided.
