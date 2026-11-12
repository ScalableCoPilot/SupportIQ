# SupportIQ — Project Instructions

## 1. Project Overview

SupportIQ is an AI-powered customer support knowledge portal.

The project aims to help support teams manage knowledge, retrieve relevant information, understand customer issues, assist support agents, and improve customer support operations.

The project must be developed through a structured, approval-driven Software Development Life Cycle (SDLC).

These instructions apply to all project activities performed using Google Antigravity or other AI development agents.

## 2. Project Technology Context

The following technology choices are the current proposed project defaults:

| Area | Proposed Technology |
|---|---|
| Backend | .NET 10 / ASP.NET Core |
| Frontend | React + TypeScript |
| UI Framework | Latest Bootstrap |
| Database | SQL Server |
| Authentication | Local database identity with JWT-based authentication |
| AI Platform | Azure AI Foundry |
| Initial Deployment | Local development environment |
| Architecture | Modular and extensible architecture |
| Multi-Tenancy | Future tenant isolation capability |

Important:
- Treat these as proposed defaults unless explicitly approved in the requirements.
- Do not silently convert technical proposals into approved requirements.
- Identify conflicts between the original baseline and proposed technology choices.
- Record unresolved technical decisions as open questions.
- Do not introduce additional technologies without justification and approval.

## 3. Shared Project Instructions

Before starting any task:

1. Read this `GEMINI.md` file.
2. Read `.github/copilot-instructions.md`.
3. Identify the task type and relevant project documentation.
4. Read the applicable skill from `.github/skills/`.
5. Review relevant prompts from `.github/prompts/`, if applicable.
6. Follow the project's documentation and approval requirements.

Do not assume that reading only one instruction file is sufficient.

## 4. Skills

### Requirements Analysis

For requirements-related activities, use:

`.github/skills/requirements-analysis/SKILL.md`

This is the common requirements lifecycle skill.

It covers:
- Baseline analysis.
- Requirements discovery.
- Stakeholder interviews.
- Business analysis.
- Functional and non-functional requirements.
- Gap and conflict analysis.
- Evidence and decision management.
- Requirements validation.
- Requirements approval.
- Final PRD generation.
- Requirements traceability.

Always read the complete skill before starting a requirements-analysis task.

Do not recreate separate requirements-interview, business-analysis, or PRD skills unless the project owner explicitly requests them.

### Other Development Skills

For implementation, testing, security, code review, architecture, or deployment tasks, use relevant available project skills when they exist.

Do not invent skill names or assume unavailable skills are installed.

## 5. Requirements and Documentation Management

The original requirements baseline is located under:

`docs/requirements/baseline/`

Use the current approved baseline file in that folder. The Markdown baseline should be used as the working source when it is the designated current version.

Never modify or overwrite the original baseline without explicit authorization.

Use the following documentation areas:

- `docs/requirements/baseline/` — original source documents.
- `docs/requirements/analysis/` — working analysis and discovery documents.
- `docs/requirements/evidence/` — evidence, assumptions, decisions, and open questions.
- `docs/requirements/approved/` — approved requirements and final PRD.

Follow the reusable requirements-analysis skill for the detailed documentation structure.

Documentation principles:
- Keep analysis separate from approved requirements.
- Maintain stable requirement IDs.
- Record source references and evidence.
- Maintain assumptions, decisions, risks, and open questions.
- Avoid duplicate or unnecessary documents.
- Update impacted documentation when requirements change.

## 6. Requirements Approval Gates

Follow these approval gates:

| Gate | Description |
|---|---|
| Gate 1 | Initial baseline analysis review |
| Gate 2 | Discovery findings review |
| Gate 3 | Requirements approval |
| Gate 4 | Final PRD review and approval |
| Gate 5 | Authorization to begin implementation planning |

Rules:
- Ask one stakeholder question at a time during discovery.
- Present findings before asking for approval.
- Do not treat a confirmation of an individual answer as approval of the complete requirements.
- Do not finalize the PRD before Gate 3 approval.
- Do not start implementation planning before Gate 5 authorization.

## 7. Development Principles

When implementation is authorized:

- Follow the approved PRD and technical decisions.
- Prefer clean, modular, maintainable code.
- Use asynchronous programming for I/O-bound operations.
- Apply appropriate dependency injection.
- Use clear separation of concerns.
- Follow secure coding practices.
- Avoid unnecessary abstractions and overengineering.
- Preserve existing approved behavior unless a change is authorized.
- Handle exceptions and validation consistently.
- Include appropriate logging and observability.
- Avoid introducing unnecessary dependencies.
- Keep changes focused on the requested task.

Do not begin implementation based on assumptions or unapproved requirements.

## 8. AI and RAG Principles

For AI-related functionality:

- Clearly define the business purpose of each AI capability.
- Document data sources and ingestion requirements.
- Identify document processing and retrieval expectations.
- Define access control for retrieved information.
- Consider tenant and data isolation.
- Address hallucination risks and unsupported answers.
- Define evaluation and monitoring requirements.
- Record unresolved RAG metrics and evaluation criteria as open questions.
- Do not invent scoring rubrics, thresholds, or accuracy targets.
- Consider data privacy, security, and retention requirements.

AI and RAG implementation details must follow approved requirements.

## 9. Security Principles

Security must be considered throughout requirements and development.

Evaluate:
- Authentication and authorization.
- Role and permission management.
- Secure API access.
- Input validation.
- Sensitive data protection.
- Secure file upload and storage.
- Audit logging.
- Tenant data isolation.
- Secrets and configuration management.
- Applicable privacy and compliance obligations.

Do not expose credentials, secrets, tokens, or sensitive customer data in source code or logs.

## 10. Git and Change Management

- Follow the repository's existing branching strategy.
- Keep changes focused and reviewable.
- Use meaningful commit messages.
- Do not overwrite unrelated changes.
- Do not delete existing project files without authorization.
- Maintain documentation consistency with code changes.
- Do not create commits, push branches, or open pull requests unless requested or authorized.

## 11. Agent Approval Rules

The project owner must remain in control of important decisions.

Request approval before:
- Changing approved requirements.
- Changing agreed technology choices.
- Introducing major architectural decisions.
- Expanding project scope.
- Changing security or authentication behavior.
- Modifying original baseline documents.
- Beginning implementation planning.
- Performing destructive operations.

## 12. General Working Instructions

For every task:

1. Understand the requested outcome.
2. Read the relevant instructions and documentation.
3. Identify constraints and dependencies.
4. Explain important findings and uncertainties.
5. Make only the changes required by the task.
6. Validate the result.
7. Summarize files created or modified.
8. Identify unresolved issues and decisions requiring approval.

Do not claim that a task, test, deployment, or approval is complete unless it has actually been completed or verified.