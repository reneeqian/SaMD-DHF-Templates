# Software Maintenance Plan — {{PROJECT_NAME}}

Per IEC 62304 §6.1. Defines the processes for maintaining the software after release,
including monitoring, bug response, end-of-life, and maintenance change control.

## 1. Scope

This plan applies to all released versions of {{PROJECT_NAME}} from initial release
through end-of-life. It covers corrective, adaptive, and perfective maintenance.

| Maintenance Type | Definition | Examples |
|---|---|---|
| Corrective | Fix defects discovered post-release | Bug fixes, anomaly resolution |
| Adaptive | Accommodate changes in the operating environment | Dependency upgrades, OS compatibility |
| Perfective | Improve performance without changing functionality | Optimization, refactoring |
| Emergency | Immediate fix for safety-critical or Critical-severity anomaly | Hotfix release |

## 2. Monitoring Activities

| Activity | Frequency | Responsible | Tool / Source |
|---|---|---|---|
| CVE scan | Every push + weekly schedule | CI | pip-audit |
| Anomaly log review | Weekly | {{ROLE}} | `11_anomaly_log/anomaly_log.md` |
| SOUP version drift check | Every CI run | CI | `soup_checker` (regulatory_tools) |
| Model performance review | See monitoring plan | {{ROLE}} | `13_ai_ml/model_performance_monitoring_plan.md` |
| User feedback review | Monthly | {{ROLE}} | {{FEEDBACK_SOURCE}} |

## 3. Maintenance Change Process

All maintenance changes follow the change control process in
`09_change_control/change_control_procedure.md`. Additionally:

1. Log the anomaly in `11_anomaly_log/anomaly_log.md` (if corrective).
2. Assess safety impact: does the change affect any RSK-* requirement?
3. If safety impact: update `04_risk_management/` records before deployment.
4. Run `python runtests.py` — must pass at Grade ≥ B with 100% requirements coverage.
5. Record the change in `09_change_control/change_log.md`.
6. Update `07_configuration_management/baseline_register.md` at release.

## 4. Supported Versions

| Version | Support Status | Support End Date |
|---|---|---|
| {{CURRENT_VERSION}} | Active — full support | {{DATE}} |
| {{PREVIOUS_VERSION}} | Security fixes only | {{DATE}} |
| Older versions | End of life — no support | — |

Users on end-of-life versions are responsible for assessing continued fitness for purpose.

## 5. Emergency Maintenance

For Critical-severity anomalies with confirmed patient safety impact:

1. Immediately notify {{RESPONSIBLE_PERSON}}.
2. Assess whether deployment must be suspended pending fix.
3. Implement hotfix on a dedicated branch; expedited review by two approvers.
4. Deploy as a patch release (X.Y.Z+1).
5. Notify affected users per the notification procedure in {{NOTIFICATION_PROCEDURE_LOCATION}}.
6. File an anomaly report and complete root-cause analysis within 30 days.

## 6. End-of-Life Policy

{{PROJECT_NAME}} version X.Y will reach end-of-life on {{EOL_DATE}}.

Prior to end-of-life:
- Notify users {{EOL_NOTICE_PERIOD}} in advance.
- Confirm all unresolved anomalies are either fixed or formally risk-accepted.
- Archive the final release artifacts and all DHF records.
- Retain records for {{RETENTION_PERIOD}} per applicable regulations.
