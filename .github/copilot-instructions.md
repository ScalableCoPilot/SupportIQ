# SupportIQ — GitHub Copilot Instructions

## 1. Project Context

SupportIQ is an AI-powered customer support knowledge portal.

The project focuses on:
- Knowledge base management.
- Document ingestion and processing.
- Retrieval-Augmented Generation (RAG).
- Ticket intelligence.
- AI-powered support agent assistance.
- Lightweight workflow automation.
- AI evaluation and operational monitoring.

Follow the approved project requirements and maintain consistency across the application.

## 2. Proposed Technology Stack

The following are the current proposed technology defaults:

| Component | Proposed Technology |
|---|---|
| Backend | .NET 10 / ASP.NET Core |
| Frontend | React + TypeScript |
| UI Framework | Latest Bootstrap |
| Database | SQL Server |
| Authentication | Local database identity with JWT-based authentication |
| AI Platform | Azure AI Foundry |
| Deployment | Local development initially |
| Architecture | Modular and extensible |
| Multi-Tenancy | Future tenant isolation capability |

Important rules:
- These choices are proposed defaults until approved.
- Do not assume every proposed choice is finalized.
- Identify conflicts between baseline requirements and proposed technology choices.
- Do not introduce alternative technologies without explaining the reason.
- Record unresolved choices as open questions.

## 3. Instruction and Skill Discovery

Before performing a task:

1. Read the root `GEMINI.md` when available.
2. Read this repository instruction file.
3. Identify the task category.
4. Read the applicable skill from `.github/skills/`.
5. Review relevant prompts under `.github/prompts/`, if applicable.
6. Follow the relevant project documentation.

For requirements-related tasks, always use:

`.github/skills/requirements-analysis/SKILL.md`

Read the complete skill before performing requirements analysis.

Do not rely on old or separate requirements-interview, business-analysis, or PRD skills when the consolidated requirements-analysis skill is available.

## 4. Source of Truth

Use the following order when determining project decisions:

1. Explicitly approved stakeholder decisions.
2. Approved requirements and PRD.
3. Confirmed requirements supported by source evidence.
4. Original baseline and supporting documents.
5. Project instructions and proposed defaults.
6. Assumptions and recommendations.

When sources conflict:
- Identify the conflict.
- Reference the affected documents or requirements.
- Do not silently choose one interpretation.
- Record the issue in the decision log or open questions register.
- Request clarification or approval.

The original baseline must not be modified without explicit authorization.

## 5. Requirements Management

All requirements-related work must follow the consolidated requirements-analysis skill.

Maintain clear separation between:

- Confirmed requirements.
- Approved requirements.
- Assumptions.
- Recommendations.
- Open questions.
- Rejected requirements.
- Deferred requirements.

Use stable requirement IDs.

Recommended identifiers:

| Prefix | Description |
|---|---|
| BR | Business Requirement |
| FR | Functional Requirement |
| NFR | Non-Functional Requirement |
| RULE | Business Rule |
| UC | Use Case |
| WF | Workflow |
| DATA | Data Requirement |
| API | API / Integration Requirement |
| AI | AI Requirement |
| US | User Story |
| AC | Acceptance Criteria |
| TC | Test Case |
| RISK | Risk |
| ASM | Assumption |
| EV | Evidence |
| Q | Open Question |
| DEC | Decision |
| CHG | Change |

Maintain traceability:

Business Requirements → Functional / Non-Functional Requirements → User Stories → Acceptance Criteria → Test Cases.

Do not invent requirements or stakeholder answers.

## 6. Requirements Approval Process

Follow these approval gates:

| Gate | Required Approval |
|---|---|
| Gate 1 | Initial baseline analysis |
| Gate 2 | Discovery findings |
| Gate 3 | Complete requirements |
| Gate 4 | Final PRD |
| Gate 5 | Implementation planning authorization |

Rules:
- Interview stakeholders one question at a time.
- Record stakeholder responses and decisions.
- Do not treat silence as approval.
- Do not finalize the PRD before requirements approval.
- Do not create an implementation plan before explicit authorization.

## 7. Backend Development Guidelines

When backend implementation is authorized:

- Use .NET 10 and ASP.NET Core according to the approved architecture.
- Prefer asynchronous APIs for I/O-bound operations.
- Use `async` and `await` correctly.
- Avoid blocking calls such as `.Result` and `.Wait()` in asynchronous request paths.
- Use dependency injection appropriately.
- Separate controllers, business logic, data access, and infrastructure concerns.
- Use DTOs and request/response models where appropriate.
- Validate incoming requests.
- Handle exceptions consistently.
- Use structured logging.
- Use configuration and environment variables for environment-specific values.
- Avoid hardcoded secrets and connection strings.
- Use cancellation tokens for long-running or I/O-bound operations where appropriate.
- Use parameterized database queries.
- Avoid unnecessary database calls and N+1 query patterns.
- Apply transactions where business consistency requires them.

Do not convert existing synchronous methods into fire-and-forget operations.

Do not use `Task.Run` as a substitute for genuinely asynchronous database or network operations.

## 8. Frontend Development Guidelines

When frontend implementation is authorized:

- Use React with TypeScript.
- Use Bootstrap for UI styling according to the approved design.
- Build reusable components where appropriate.
- Use clear component and folder organization.
- Keep API communication separate from presentation logic.
- Handle loading, empty, success, and error states.
- Validate user inputs.
- Follow accessibility and responsive design practices.
- Avoid unnecessary dependencies and duplicate components.
- Follow the approved authentication and authorization flow.

Do not introduce a new frontend framework without approval.

## 9. Database Guidelines

- Use SQL Server according to the approved database design.
- Use appropriate primary keys, foreign keys, indexes, and constraints.
- Avoid duplicate or unnecessary data.
- Use parameterized queries.
- Consider query performance and expected data volume.
- Document important schema decisions.
- Maintain data integrity.
- Consider data retention, archival, and deletion requirements.
- Do not execute destructive database changes without authorization.

## 10. AI and RAG Development Guidelines

For AI and RAG features:

- Follow approved AI requirements and data-access rules.
- Keep document ingestion, parsing, chunking, embedding, retrieval, and generation responsibilities clear.
- Preserve source references for retrieved content.
- Enforce authorization and data isolation during retrieval.
- Handle unsupported questions and insufficient context.
- Do not present generated answers as verified facts without supporting evidence.
- Log relevant evaluation and operational information without exposing sensitive data.
- Make model and prompt configuration maintainable.
- Consider cost, latency, reliability, and failure handling.
- Do not invent RAG evaluation metrics, thresholds, or scoring rubrics.

Any unresolved AI design decision must remain documented until approved.

## 11. Security Guidelines

- Follow secure coding practices.
- Validate and sanitize user input.
- Apply authentication and authorization to protected endpoints.
- Store passwords using appropriate identity password hashing.
- Protect secrets and sensitive configuration.
- Secure uploaded files and validate file types and sizes.
- Prevent unauthorized access to customer and tenant data.
- Apply appropriate API security controls.
- Avoid logging credentials, tokens, or sensitive personal information.
- Consider audit logging and security monitoring.

Security-related changes must follow approved requirements.

## 12. Testing Guidelines

For implementation changes:

- Add unit tests for business logic where appropriate.
- Add integration tests for important API and database behavior.
- Test validation and error scenarios.
- Test authorization and access boundaries.
- Test important AI and retrieval behaviors against approved evaluation criteria.
- Avoid changing unrelated tests.
- Run relevant tests after modifying code.
- Report test failures accurately.

Do not claim tests passed unless they were actually executed successfully.

## 13. Code Change Rules

- Make the smallest appropriate change.
- Preserve existing behavior unless a change is authorized.
- Follow existing naming and coding conventions.
- Avoid unnecessary refactoring.
- Avoid modifying unrelated files.
- Do not introduce unnecessary packages.
- Do not duplicate existing functionality.
- Explain significant design decisions.
- Keep changes reviewable and maintainable.

Before changing shared interfaces or public contracts, identify affected consumers and request approval when required.

## 14. Git and Pull Request Guidelines

- Follow existing repository branching conventions.
- Use meaningful commit messages.
- Keep pull requests focused.
- Include a clear summary of changes.
- Include testing information.
- Identify configuration or migration requirements.
- Do not commit secrets or generated sensitive files.
- Do not commit, push, merge, or open pull requests without the required authorization.

## 15. Documentation Guidelines

Keep documentation aligned with the application.

Use:

- `docs/requirements/baseline/` for original source documents.
- `docs/requirements/analysis/` for working analysis.
- `docs/requirements/evidence/` for evidence, decisions, assumptions, and questions.
- `docs/requirements/approved/` for approved requirements and PRD.

Do not overwrite the baseline.

Avoid unnecessary documentation and duplicate information.

Update relevant documentation when approved requirements or implementation behavior changes.

## 16. Agent Approval and Restrictions

Request explicit approval before:
- Changing approved requirements.
- Changing the agreed technology stack.
- Introducing major architectural decisions.
- Expanding project scope.
- Changing authentication or authorization behavior.
- Modifying the original baseline.
- Performing destructive database or file operations.
- Starting implementation planning.
- Committing, pushing, or merging changes when not already authorized.

Do not:
- Invent business requirements.
- Treat assumptions as approved facts.
- Ignore unresolved conflicts.
- Bypass approval gates.
- Implement unapproved features.
- Claim completion without verification.

## 17. Expected Copilot Response

For substantial tasks, structure the response as follows:

1. Understanding of the request.
2. Relevant existing files and dependencies.
3. Proposed approach.
4. Approval needed, if applicable.
5. Files to be created or modified.
6. Implementation or documentation changes.
7. Validation and test results.
8. Remaining questions or risks.

For small questions or focused code changes, keep the response concise and avoid unnecessary reports.