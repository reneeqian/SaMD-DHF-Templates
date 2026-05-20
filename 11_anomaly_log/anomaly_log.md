# Anomaly Log — {{PROJECT_NAME}}

Formal problem resolution record per IEC 62304 §9.

All software anomalies (defects, unexpected behaviors, test failures, safety-relevant
deviations) shall be entered here upon discovery. Each anomaly must be triaged, tracked
to closure, and reviewed for safety impact before release.

Intentional changes (new features, planned refactors) belong in
`09_change_control/change_log.md`, not here.

## Severity Definitions

| Severity | Criteria |
|---|---|
| Critical | Potential patient harm; safety-critical path affected; must be resolved before any release |
| High | Incorrect output; data loss; significant functional gap; resolve before next release |
| Medium | Incorrect behavior with workaround available; degraded performance; resolve within 90 days |
| Low | Cosmetic, documentation, or minor UX issue; resolve in next planned release |

## Anomaly Table

| ID | Discovered | Severity | Status | Description | Safety Impact | Resolution | Linked PR | Closed |
|---|---|---|---|---|---|---|---|---|
| ANO-001 | {{DATE}} | {{SEVERITY}} | Open / Closed | {{DESCRIPTION}} | {{YES_NO}} — {{IMPACT_RATIONALE}} | {{RESOLUTION}} | {{PR_LINK}} | {{DATE}} |

## Status Definitions

| Status | Meaning |
|---|---|
| Open | Anomaly confirmed; under investigation or awaiting fix |
| In Progress | Fix being developed |
| Resolved | Fix implemented and merged; pending verification |
| Closed | Verified fixed; closure date recorded |
| Deferred | Accepted risk; documented rationale required |
| Not Reproducible | Cannot confirm; monitoring for recurrence |

## Unresolved Anomalies at Release

Per FDA 510(k) submission requirements, all unresolved anomalies at the time of submission
must be listed below with a rationale for why each does not pose unacceptable risk.

| ANO-ID | Severity | Rationale for Deferral |
|---|---|---|
| — | — | — |

*If this table is empty, there are no known unresolved anomalies at submission.*
