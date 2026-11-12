# ADR-002: Azure AI Search for knowledge retrieval

## Status

Accepted

## Context

SupportIQ's approved first-release scope includes permission-scoped retrieval over knowledge content and grounded answers generated with Azure AI Foundry. A search/index service is needed to support keyword and vector retrieval. The service and resource configuration had not been selected in the implementation plan.

## Decision

Use Azure AI Search as the knowledge search/index service for keyword and vector retrieval. Apply tenant, role, content lifecycle, and external-publication constraints to retrieval as required by the approved requirements. Resolve index schema, embedding-model compatibility, resource configuration, and provisioning separately before integration work depends on them.

## Consequences

- Search is an explicit managed Azure dependency and adds configuration and operating cost.
- Search results must be constrained by server-authorized tenant, role, and publication scope; an index filter is not a replacement for API authorization.
- Local-development connection strategy, resource provisioning, index schema, and exact embedding model remain open.
- This decision does not select file storage or background processing.

## Approval

Project owner approval recorded as DEC-045 / EV-071 on 2026-11-12.
