# SupportIQ API and data contract draft

## Status

Draft for detailed design. This document maps approved requirements and owner decisions into an initial contract. It does not change the approved first-release scope. Endpoint paths and payloads remain proposals unless explicitly marked as owner-approved; they must be reviewed before feature endpoints are implemented.

## Contract principles

- HTTP API prefix: `/api/v1`.
- Use JSON for request/response data and `multipart/form-data` for a single document upload.
- Use ASP.NET Core `ProblemDetails` for errors; responses must not reveal credentials, security stamps, tenant content, or internal exception details.
- Require bearer authentication except for health and token issuance.
- Resolve tenant scope from the authenticated identity and current active membership. Never authorize from a caller-supplied tenant ID in a route, query, header, or body.
- An internal user has active membership in one tenant only (DEC-053). External customer tenant association is bound to the authenticated account. Platform Admin has no tenant-content access.
- Check the current Identity security stamp for authenticated requests. Changing it revokes all access tokens for that user (DEC-052).
- JWT access-token expiry is configurable, with no default lifetime selected. No refresh tokens are issued in the first release; the user authenticates again after expiry (DEC-051).
- Return a correlation/trace identifier for support. Do not log passwords, tokens, document contents, or customer data.
- Enforce the approved maximum upload size as 10,000,000 bytes per file (decimal MB; DEC-055).

## Initial endpoint groups

All paths and schemas are proposed for owner review. Routes do not accept a tenant identifier supplied by a caller.

| Area | Proposed operation | Authorization and behavior |
|---|---|---|
| Health | `GET /health` | Liveness only; returns service status and does not expose dependency configuration. |
| Authentication | `POST /api/v1/auth/token` | Route approved under DEC-056. Accepts email address and password (DEC-054); issues a JWT only for a valid active account/membership. Does not provide account registration or invitation. |
| Authentication | `GET /api/v1/auth/me` | Returns the authenticated user's safe identity, role, and server-derived tenant context. |
| Authentication | `POST /api/v1/auth/logout` | Changes the current user's Identity security stamp, revoking all of that user's active JWTs. |
| Membership | `/api/v1/members` | Tenant Admin manages only members in the authenticated tenant; invitation and approval workflow remains deferred. |
| Knowledge documents | `/api/v1/knowledge/documents` | Authenticated, authorized users upload one file per request; per-file maximum is 10,000,000 bytes (DEC-040/DEC-055). A successful asynchronous submission returns an operation/document identifier and processing status. |
| Knowledge documents | `/api/v1/knowledge/documents/{documentId}` | Reads status/metadata only within the authenticated tenant. |
| Knowledge documents | `/api/v1/knowledge/documents/{documentId}/reprocess` | Requests authorized reprocessing; duplicate delivery must not duplicate derived content. |
| Knowledge articles | `/api/v1/knowledge/articles` | Tenant-scoped author/read operations follow role and content-lifecycle rules. |
| Knowledge articles | `/api/v1/knowledge/articles/{articleId}/review` | Support Manager or explicitly authorized role performs review/publication transitions; authors cannot approve, reject, or publish. |
| Assistant | `/api/v1/assistant/conversations` | Creates or lists conversations within the authenticated user/tenant scope. |
| Assistant | `/api/v1/assistant/conversations/{conversationId}/messages` | Adds a message and returns a grounded answer with source references or an explicit abstention/failure response. |
| Assistant | `/api/v1/assistant/conversations/{conversationId}/escalation` | Escalates an unanswered conversation; only authorized Support Agents can view/respond to escalated work. |
| Platform operations | `/api/v1/platform/operations` | Platform Admin may access only the allowlisted platform metadata; tenant business content is prohibited. |

Exact route methods, payload properties, pagination, update/delete semantics, status-transition matrix, and invitation flow remain subject to review and detailed design. External-customer registration/verification is not included in this contract.

## Authentication contract

### Token issuance

Approved request field names (DEC-058):

```json
{
  "email": "user@example.test",
  "password": "user supplied password"
}
```

Approved response shape (DEC-057):

```json
{
  "accessToken": "signed JWT",
  "tokenType": "Bearer",
  "expiresAtUtc": "configured expiry",
  "user": {
    "userId": "identity id",
    "userName": "identity user name",
    "tenantId": "server-derived tenant id or null for platform-only identity",
    "roles": ["role"]
  }
}
```

JWTs must carry `UserId`, `UserName`, `Role`, and `exp`; tenant-scoped identities also carry `TenantId`. Platform Admin JWTs omit `TenantId` as an approved amendment to FR-OP-14 (DEC-060). `TenantId` and `Role` are validated server-side for authorization where applicable. The token must bind to the current user security stamp without exposing the raw stamp as a response field. Exact issuer, audience, signing-key source, lifetime value, and permitted clock skew must be explicit configuration/design decisions; the JWT must preserve the approved claim names on the wire. No secrets or example keys are committed. Sign-in resolves by normalized email. For invalid credentials, return the same generic authentication error whether the email is unknown or the password is wrong (DEC-059).

No registration, password-reset, email-verification, refresh-token, or invitation endpoint is defined here. Those workflows remain deferred.

## Error behavior

Use `application/problem+json` with stable machine-readable `type`, `title`, `status`, and a correlation identifier. Validation errors may include field-level details that do not disclose secrets.

| Status | Meaning |
|---|---|
| `400` | Malformed request or validation failure |
| `401` | Missing, invalid, expired, or revoked authentication |
| `403` | Authenticated identity lacks the required role/action |
| `404` | Resource not found in the caller's authorized scope |
| `409` | Invalid lifecycle transition or conflicting state |
| `413` | Request exceeds the approved upload limit |
| `415` | Unsupported content type |
| `500` / `503` | Unexpected or dependency failure; return a safe error and correlation identifier |

Exact error codes, retryability, rate limits, and dependency timeout budgets remain open. A failed operation must never return a success-shaped response.

## Data and asynchronous-processing boundaries

- SQL Server/Azure SQL is the system of record, using EF Core. The final schema and migrations remain to be designed.
- Store source files in Azure Blob Storage. Store only metadata and a storage reference in the relational database; do not put document content in queue messages.
- Use Azure AI Search for keyword/vector retrieval. Search filters are not a substitute for API authorization; tenant, role, lifecycle, and publication constraints must be applied on every retrieval.
- The API submits a versioned Service Bus job containing identifiers and correlation metadata, not document contents or credentials. The API derives tenant context from authenticated membership.
- Azure Functions process jobs idempotently; exact message schema, retries, dead-letter policy, and namespace/queue configuration remain open.
- After 90 days from original upload, delete source document, extracted text, chunks, and embeddings from Blob Storage, SQL, and the search index. Backup and log/evaluation retention remain open.
- Authentication, membership, content, and lifecycle changes that require auditability must be traceable without logging sensitive payloads.

## Decisions that remain open

- Issuer/audience, configurable token lifetime, signing-key source, and clock skew.
- Detailed membership/invitation workflow and role assignment.
- Entity fields, database constraints, indexes, migration rollout, and transaction boundaries.
- Full document metadata, parser support, operation-status schema, and manual deletion behavior.
- Search index schema and Foundry embedding/model deployment compatibility.
- Service Bus message schema, retries/dead-letter behavior, and local/hosted resource configuration.
- Conversation-history retention/deletion and non-document retention policies.
- Rate limits, pagination/filtering conventions, timeout budgets, and numeric service targets.

## Traceability

| Contract area | Approved trace |
|---|---|
| Tenant/role authorization | API-001, `FR-CA-14`, `FR-OP-09`, `FR-OP-14`, `RULE-010`–`RULE-015`, AC-006, AC-007, AC-010; DEC-009, DEC-020, DEC-041, DEC-053, DEC-060 |
| Authentication and session | `FR-OP-10`–`FR-OP-11`, AC-010; DEC-009, DEC-011, DEC-012, DEC-051, DEC-052, DEC-056 |
| Knowledge upload and lifecycle | `FR-KB-01`–`FR-KB-17`, DATA-002, AC-009, AC-014; DEC-028, DEC-040 |
| Grounded assistant and history | `FR-CA-01`–`FR-CA-16`, AI-001, AC-001–AC-005 |
| Platform boundary | ROLE-004, `RULE-010`–`RULE-011`, AC-007; DEC-002, DEC-003 |
