# ADR-003: Azure Blob Storage for source documents

## Status

Accepted

## Context

SupportIQ must retain uploaded source documents and delete source and derived content after the approved 90-day retention period. Local development precedes a hosted Azure demonstration. The storage provider had not been selected.

## Decision

Use Azure Blob Storage for source documents in both local development and hosted Azure environments. Local development will connect to an Azure development storage account rather than use a local emulator. Verify account availability and configuration before integration; resource provisioning remains separately gated.

## Consequences

- The application uses one storage provider across environments.
- Local development depends on an available Azure development storage account; no account was verified in this decision.
- Storage credentials and endpoints must be supplied through secure environment configuration, never committed to source.
- This decision does not select background processing, search/index configuration, or document metadata persistence.
- No Azure resource provisioning is authorized by this decision.

## Approval

Project owner approval recorded as DEC-046 / EV-072 on 2026-11-12.

The local connection approach was selected under DEC-047 / EV-073 on 2026-11-12. Account availability remains unverified.
