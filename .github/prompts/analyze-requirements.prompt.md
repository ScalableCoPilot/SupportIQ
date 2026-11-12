---
name: Analyze Requirements
description: Analyze the project baseline, identify requirements gaps, conduct stakeholder discovery, maintain evidence, and prepare approved requirements and PRD.
agent: agent
---

# Start Requirements Analysis

Start the requirements-analysis lifecycle for the current project.

## 1. Read Project Instructions

Before starting:

1. Read the root `GEMINI.md`, if available.
2. Read `.github/copilot-instructions.md`, if available.
3. Read the complete `.github/skills/requirements-analysis/SKILL.md`.
4. Review relevant project documentation and supporting instructions.

Follow the project-specific instructions together with the requirements-analysis skill.

## 2. Locate Source Documents

Identify the original requirements baseline and supporting documents.

Prefer the project's configured baseline location.

For SupportIQ, the baseline is located under:

`docs/requirements/baseline/`

Do not assume this location for other projects if their instructions specify a different location.

Read and analyze the available source documents completely.

Do not modify or overwrite original source documents.

## 3. Analyze Requirements

Perform a comprehensive requirements analysis.

Identify:

- Business objectives and expected outcomes.
- Project scope and exclusions.
- Stakeholders and user roles.
- Existing business workflows.
- Functional requirements.
- Non-functional requirements.
- Business rules.
- Data requirements.
- API and integration requirements.
- Technical constraints and dependencies.
- AI and specialized requirements, where applicable.
- Missing, incomplete, ambiguous, and conflicting requirements.
- Assumptions, risks, and open questions.

Clearly distinguish confirmed information from assumptions, proposals, and recommendations.

Do not invent requirements or silently resolve conflicts.

## 4. Create Analysis and Evidence Documents

Create or update the necessary documentation under the project's requirements documentation structure.

Maintain:

- Baseline analysis.
- Requirements inventory.
- Gap and conflict analysis.
- Stakeholder and discovery findings.
- Business and system requirements.
- Evidence register.
- Assumptions register.
- Decision log.
- Open questions register.
- Risks and dependencies.
- Requirements traceability.

Reuse existing documents where appropriate.

Do not create unnecessary duplicate or empty files.

## 5. Stakeholder Discovery

After presenting the initial analysis:

- Interview me one question at a time.
- Ask the highest-impact unresolved question first.
- Explain why clarification is required when useful.
- Wait for my response before asking the next question.
- Record my answers accurately.
- Update the affected requirements and evidence documents.
- Keep unresolved matters in the open questions register.

Do not repeatedly ask questions already answered by reliable evidence.

## 6. Follow Approval Gates

Follow all approval gates defined in the requirements-analysis skill.

In particular:

- Do not treat individual answers as approval of the complete requirements.
- Do not finalize requirements without explicit stakeholder approval.
- Do not generate the final PRD before requirements approval.
- Do not start implementation planning before separate explicit authorization.

Present findings and request approval at each required gate.

## 7. Expected Initial Response

Start by:

1. Confirming the project context.
2. Listing the source documents identified.
3. Presenting the initial baseline analysis.
4. Highlighting missing, incomplete, ambiguous, and conflicting requirements.
5. Identifying assumptions, risks, and major dependencies.
6. Listing the initial open questions.
7. Identifying the most important clarification needed.

Then ask only the first most important stakeholder question and wait for my response.

Do not generate the final PRD or implementation plan at this stage.