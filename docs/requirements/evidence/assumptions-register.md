# SupportIQ Assumptions Register

## Status

Only assumptions stated or directly indicated in the baseline are recorded here. They are unvalidated unless a later stakeholder response changes their status. Project instructions’ proposed technology defaults are recorded as proposals/open questions, not assumptions or decisions.

| ID | Assumption | Reason/source | Impact if incorrect | Validation owner | Status |
|---|---|---|---|---|---|
| ASM-001 | CloudDesk is fictional and demo/sample data is synthetic. | Baseline Section 17 labels CloudDesk fictional and data synthetic; Executive Summary and Confirmed Baseline Decisions also state synthetic data. | Use of real customer data would change privacy, security, compliance, and testing needs. | Project owner | Pending Gate 1 confirmation; source-supported but not stakeholder-approved |
| ASM-002 | Required Azure AI model and search resources will be available for the intended region, quota, model, and cost. | Baseline Section 17 explicitly lists resource availability as an assumption and asks to confirm region, model availability, quotas, and cost. | AI/search functionality, schedule, and budget may be infeasible or need approved alternatives. | Project owner / resource owner not identified | Unvalidated |

## Related proposals not classified as assumptions

- The baseline suggests a deterministic synthetic ticket seed script as a preference; the project owner deferred ticket taxonomy, fields, and seed strategy until ticket AI and analytics are included in a future phase.
- Sample dataset counts and the 30-day delivery boundary are suggested baseline targets.
- The repository instructions’ technology stack is explicitly proposed until approved.

These are tracked as open questions or source proposals rather than being promoted to assumptions.
