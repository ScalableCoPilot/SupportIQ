# ADR-004: Queue-triggered document processing

## Status

Accepted

## Context

Document extraction, normalization, chunking, embedding, and indexing are asynchronous operations. The implementation plan left the worker mechanism open. The project owner selected a separate Azure Function triggered by an Azure Service Bus queue instead of an API-hosted SQL job worker.

## Decision

Use an Azure Function with an Azure Service Bus queue trigger to process document jobs. Define the message contract, namespace/queue configuration, retry/dead-letter behavior, idempotency, and monitoring before implementing the processing pipeline or provisioning resources. Locally running Functions will connect to a dedicated Azure development Service Bus namespace (DEC-049); its availability/configuration has not been verified.

## Consequences

- Document-processing capacity can scale separately from the API.
- The solution adds an independently configured Function and Service Bus dependency.
- The API and worker must share stable, versioned job contracts and handle duplicate delivery safely.
- Local development requires a configured connection to a dedicated Azure development Service Bus namespace; the namespace has not been verified.
- No Azure resource provisioning is authorized by this decision.

## Approval

Project owner approval recorded as DEC-048 / EV-074 on 2026-11-12.

The local connection approach was selected under DEC-049 / EV-075 on 2026-11-12. Namespace availability and configuration remain unverified.
