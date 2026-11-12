# ADR-007: Single-tenant membership for internal users

## Status

Accepted

## Context

SupportIQ requires server-derived tenant isolation. Internal identity claims include tenant and role context, while the initial requirements did not say whether an internal account could belong to multiple tenants.

## Decision

An internal support user may have active membership in one tenant only. The API derives `TenantId` and role claims from that active membership. External customer tenant association is also resolved from the authenticated account. Callers cannot select or override tenant scope through request headers or parameters.

## Consequences

- A single tenant context can be included in an internal user's access token without a tenant-selection workflow.
- Membership deactivation and role changes must invalidate or deny prior authorization; token validation must use current Identity state as defined by ADR-006.
- Platform Admin is a separate platform role and cannot use this decision to access tenant business content.
- A future multi-tenant internal-user requirement would require a separately approved change and explicit tenant-switching design.

## Approval

Project owner approval recorded as DEC-053 / EV-079 on 2026-11-12.
