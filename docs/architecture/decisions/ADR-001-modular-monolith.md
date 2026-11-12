# ADR-001: Modular monolith backend

## Status

Accepted

## Context

SupportIQ is starting its first demonstrable release with a small initial codebase and a single ASP.NET Core API. The domain includes identity, tenant membership, knowledge lifecycle, retrieval, conversations, escalation, and platform operations. Search, storage, and background-processing services remain undecided.

## Decision

Use one ASP.NET Core API deployment organized into feature-oriented modules. Keep the React + TypeScript frontend as a separate application. Within the API, keep HTTP endpoints, application workflows, domain rules, and infrastructure concerns separated where the behavior warrants it; do not introduce service-per-feature deployments at this stage. As a separately approved integration boundary, asynchronous document processing runs in an Azure Function triggered by Azure Service Bus (ADR-004).

## Consequences

- Local development and deployment have fewer moving parts than a microservices architecture.
- Feature boundaries can be established in code without committing to network contracts or distributed transactions between services.
- Backend modules deploy and scale together; independent deployment and scaling are not available.
- The document-processing worker is a separately deployed Azure integration, not a service-per-domain decomposition of the API.
- Search, file storage, background processing, database access details, and Azure resource topology remain separate decisions and are not implied by this ADR.

## Approval

Project owner approval recorded as DEC-044 / EV-070 on 2026-11-12. The separately hosted document-processing worker was approved under DEC-048 / EV-074.
