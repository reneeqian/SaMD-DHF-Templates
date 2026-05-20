# Model Performance Monitoring Plan — {{PROJECT_NAME}}

Per FDA AI/ML SaMD Guidance (2021) §VI. Describes how post-market model performance
is tracked, how drift is detected, and when retraining or re-submission is triggered.

## 1. Monitored Metrics

| Metric | Description | Baseline Value | Alert Threshold | Critical Threshold |
|---|---|---|---|---|
| {{METRIC_1}} | {{DESCRIPTION}} | {{BASELINE}} | {{ALERT}} | {{CRITICAL}} |
| {{METRIC_2}} | {{DESCRIPTION}} | {{BASELINE}} | {{ALERT}} | {{CRITICAL}} |
| Input distribution drift | Statistical distance between incoming data and training distribution | — | p < 0.05 (KS test) | p < 0.01 |

**Alert threshold:** triggers internal review within 5 business days.
**Critical threshold:** triggers immediate suspension of deployment pending root-cause analysis.

## 2. Data Collection for Monitoring

| Source | Data Collected | Frequency | Retention |
|---|---|---|---|
| Production inference logs | Input hash, output value, timestamp, software version | Every inference | {{RETENTION_PERIOD}} |
| User feedback / corrections | Flagged outputs, clinician overrides | Continuous | {{RETENTION_PERIOD}} |
| {{EXTERNAL_SOURCE}} | {{DESCRIPTION}} | {{FREQUENCY}} | {{RETENTION}} |

Inference logs must include: software artifact hash, input identifier, timestamp, output
value, and confidence score (if applicable). See `10_software_development_plan/sdp.md` §8
for the audit logging requirement.

## 3. Monitoring Schedule

| Activity | Frequency | Responsible |
|---|---|---|
| Automated metric dashboard review | Weekly | {{ROLE}} |
| Formal performance report | Quarterly | {{ROLE}} |
| Full distribution drift analysis | Every 6 months | {{ROLE}} |
| Post-incident review | Within 5 days of any alert | {{ROLE}} |

## 4. Retraining Triggers

Retraining is initiated when **any** of the following occur:

1. A monitored metric crosses the Alert threshold for two consecutive review periods.
2. A monitored metric crosses the Critical threshold at any point.
3. Input distribution drift is confirmed by statistical test.
4. A new patient subgroup or acquisition protocol is added to the intended use.
5. A systematic labeling error is discovered in the original training data.

All retraining events must be documented in `09_change_control/change_log.md` and
evaluated against the Predetermined Change Control Plan before deployment.

## 5. Re-Submission Triggers

A new 510(k) or supplement is required when retraining results in:
- Performance outside the pre-specified bounds in `13_ai_ml/predetermined_change_control_plan.md` §4
- A change to the intended use or patient population
- A change to a locked architectural component beyond the scope of the PCCP

## 6. Responsible Persons

| Activity | Responsible | Escalation |
|---|---|---|
| Day-to-day monitoring | {{MONITORING_ROLE}} | {{ESCALATION_CONTACT}} |
| Alert response | {{ALERT_ROLE}} | {{ESCALATION_CONTACT}} |
| Retraining decision | {{DECISION_ROLE}} | Regulatory counsel |
| Re-submission decision | {{SUBMISSION_ROLE}} | Regulatory counsel |
