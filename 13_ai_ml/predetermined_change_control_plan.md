# Predetermined Change Control Plan — {{PROJECT_NAME}}

Per FDA Guidance: Artificial Intelligence and Machine Learning in Software as a Medical
Device (2021), adaptive AI/ML devices must describe the types of anticipated modifications
and the controls that ensure continued safety and effectiveness.

## 1. Scope

This plan covers anticipated modifications to the {{PROJECT_NAME}} algorithm that may
occur post-market without a new 510(k) submission, provided they remain within the
pre-specified bounds defined below.

## 2. Types of Anticipated Modifications

| Modification Type | Description | Requires New Submission? |
|---|---|---|
| Performance optimization | Re-training on expanded dataset with same architecture; performance improves within bounds | No — if within §4 bounds |
| Architecture update | Change to model layers, hyperparameters, or preprocessing pipeline | Evaluate per §3 criteria |
| New patient population | Extension to demographics not in original training data | Likely yes |
| New intended use | Application to a different clinical task | Yes — always |
| Input data format change | New imaging modality, resolution, or acquisition protocol | Evaluate per §3 criteria |

## 3. Change Evaluation Criteria

A planned modification does **not** require a new 510(k) if **all** of the following hold:

1. The intended use and indications remain unchanged.
2. The modification does not affect safety-critical risk controls (RSK-* requirements).
3. Post-change performance on the locked test set remains within the bounds in §4.
4. The modification type is listed in §2 as "No — if within bounds."
5. The change is documented in `09_change_control/change_log.md` with the evaluation rationale.

If any criterion fails, engage regulatory counsel before deployment.

## 4. Pre-Specified Performance Bounds

These bounds were established at the time of initial submission and represent the
acceptable performance envelope for algorithm updates without re-submission.

| Metric | Pre-Submission Value | Acceptable Deviation | Measurement Dataset |
|---|---|---|---|
| {{METRIC_1}} | {{VALUE_1}} | {{BOUND_1}} | {{TEST_SET_DESCRIPTION}} |
| {{METRIC_2}} | {{VALUE_2}} | {{BOUND_2}} | {{TEST_SET_DESCRIPTION}} |

*If post-change performance falls outside these bounds, treat the modification as a new
submission candidate.*

## 5. Locked Test Set

Performance evaluation for change control uses a locked, held-out test set that is
never used for training or hyperparameter selection.

| Dataset | Version | Location | SHA-256 |
|---|---|---|---|
| {{TEST_SET_NAME}} | {{VERSION}} | {{LOCATION}} | {{HASH}} |

The test set is frozen at initial submission and must not be modified. Any change to the
test set composition requires regulatory counsel review.

## 6. Monitoring Triggers for Unplanned Changes

If post-market monitoring (see `13_ai_ml/model_performance_monitoring_plan.md`) detects:
- Performance degradation outside the bounds in §4
- A clinically significant change in output distribution
- New failure modes not present in the original hazard analysis

...then a formal change assessment must be initiated, and a new submission may be required.
