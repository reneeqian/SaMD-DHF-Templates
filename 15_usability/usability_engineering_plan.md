# Usability Engineering Plan — {{PROJECT_NAME}}

Per IEC 62366-1:2015. Defines the human factors and usability engineering activities
for {{PROJECT_NAME}}.

## 1. Intended Use Context Summary

| Element | Description |
|---|---|
| Intended users | {{CLINICIAN_TYPE}} with {{EXPERIENCE_LEVEL}} |
| Use environment | {{ENVIRONMENT}} (e.g., radiology reading room, ICU, outpatient clinic) |
| User interface | {{UI_TYPE}} (e.g., DICOM viewer plugin, web dashboard, CLI report) |
| Frequency of use | {{FREQUENCY}} |
| Time pressure | {{TIME_PRESSURE}} (e.g., acute, elective) |

## 2. User Tasks

Tasks were identified through {{TASK_ANALYSIS_METHOD}} (e.g., contextual inquiry, workflow
interviews, literature review).

| Task ID | Task Description | Safety-Critical? | Failure Consequence |
|---|---|---|---|
| T-001 | {{TASK_DESCRIPTION}} | {{YES_NO}} | {{CONSEQUENCE}} |
| T-002 | Review AI output and decide on clinical action | Yes | Over-reliance on incorrect output → missed diagnosis |
| T-003 | Override or dismiss AI recommendation | Yes | Dismissal of correct output → missed diagnosis |

Safety-critical tasks are those where a use error could directly cause or contribute to
patient harm. All safety-critical tasks require formative evaluation.

## 3. Known Use Errors and Hazard-Related Use Scenarios

| ID | Use Error | Probability | Harm | Mitigation |
|---|---|---|---|---|
| UE-001 | Over-reliance on AI output without independent clinical assessment | {{PROBABILITY}} | Missed diagnosis or over-treatment | UI: prominent "advisory only" label; no action required for dismissal |
| UE-002 | Misinterpretation of confidence score or uncertainty indicator | {{PROBABILITY}} | Inappropriate clinical action | Training; clear labeling of confidence metric |
| UE-003 | {{USE_ERROR}} | {{PROBABILITY}} | {{HARM}} | {{MITIGATION}} |

## 4. Formative Evaluation

Formative studies are conducted iteratively during development to identify and address
use errors before summative testing.

| Study | Method | Participants | Status |
|---|---|---|---|
| Prototype review | Heuristic evaluation by {{EVALUATOR_TYPE}} | {{N}} | {{STATUS}} |
| Think-aloud session | Simulated use with representative users | {{N}} | {{STATUS}} |
| {{STUDY_NAME}} | {{METHOD}} | {{N}} | {{STATUS}} |

Findings from formative evaluation are documented as anomalies in
`11_anomaly_log/anomaly_log.md` with category "Usability."

## 5. Summative Evaluation

Summative testing is conducted on the final design to demonstrate that the intended
users can use the device safely and effectively for its intended use.

| Element | Description |
|---|---|
| Participants | {{N}} representative users: {{PARTICIPANT_DESCRIPTION}} |
| Test environment | {{ENVIRONMENT}} (simulated / actual clinical setting) |
| Scenarios tested | All safety-critical tasks in §2; all high-probability use errors in §3 |
| Acceptance criteria | Zero critical use errors; {{THRESHOLD}} for non-critical use errors |
| Planned date | {{DATE}} |

## 6. Training and Labeling

| Control | Description |
|---|---|
| Labeling | IFU includes: intended use, indications, contraindications, advisory-only statement |
| On-screen warnings | {{UI_WARNING_DESCRIPTION}} |
| User training | {{TRAINING_DESCRIPTION}} |
| Training verification | {{TRAINING_VERIFICATION}} (e.g., competency assessment, attestation) |
