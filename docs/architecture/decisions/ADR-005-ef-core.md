# ADR-005: Entity Framework Core for relational persistence

## Status

Accepted

## Context

SupportIQ uses SQL Server/Azure SQL and approved ASP.NET Core Identity/JWT. The persistence library had not been selected. Identity's standard relational integration and schema migrations are important for the initial implementation.

## Decision

Use Entity Framework Core with the SQL Server provider for application persistence and ASP.NET Core Identity. Keep database schema and entity design aligned with the approved requirements and detailed API/data contracts.

## Consequences

- Identity and application persistence can share the supported EF Core ecosystem and migration mechanism.
- Query behavior must be reviewed for correctness and efficiency; complex SQL can still be used deliberately when justified.
- Database schema changes require reviewed migrations; destructive changes require explicit authorization.
- This decision does not define the schema, connection endpoints, credentials, or deployment resources.

## Approval

Project owner approval recorded as DEC-050 / EV-076 on 2026-11-12.
