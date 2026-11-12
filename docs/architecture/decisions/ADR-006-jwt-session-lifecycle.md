# ADR-006: JWT session renewal and revocation

## Status

Accepted

## Context

SupportIQ uses JWT access tokens with configurable expiry. The project owner deferred refresh-token use and revocation details to implementation design. The first release needs a clear renewal and revocation behavior without choosing an access-token lifetime prematurely.

## Decision

- Do not issue refresh tokens in the first release. Users renew access by authenticating again after the configured JWT access token expires.
- Revoke all active tokens for a user by changing the user's ASP.NET Core Identity security stamp.
- Validate the stamp on authenticated requests by comparing the stamp associated with the validated token to the current user stamp.
- Keep access-token expiry configurable; no fixed lifetime is selected by this ADR.

## Consequences

- No refresh-token storage, rotation, or refresh endpoint is required in the first release.
- User-wide revocation is straightforward, but does not revoke a single token independently.
- Immediate revocation requires current Identity state to be checked for authenticated requests; its database impact must be tested, and any caching or reduced validation frequency requires explicit review because it weakens revocation immediacy.
- Access-token duration remains configurable and must be supplied through secure configuration.

## Approval

Project owner approval recorded as DEC-051 / EV-077 and DEC-052 / EV-078 on 2026-11-12.
