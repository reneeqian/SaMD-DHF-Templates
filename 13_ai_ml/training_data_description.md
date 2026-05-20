# Training Data Description — {{PROJECT_NAME}}

Per FDA AI/ML SaMD Guidance (2021) §III. Documents the provenance, composition,
and known limitations of all data used to train and validate the algorithm.

## 1. Dataset Overview

| Dataset | Role | Size | Source | Version / Date Frozen |
|---|---|---|---|---|
| {{DATASET_1}} | Training | {{N}} cases | {{SOURCE}} | {{VERSION}} |
| {{DATASET_2}} | Validation (tuning) | {{N}} cases | {{SOURCE}} | {{VERSION}} |
| {{DATASET_3}} | Test (locked) | {{N}} cases | {{SOURCE}} | {{VERSION}} |

The test set is locked and never used for training or hyperparameter selection.
See `13_ai_ml/predetermined_change_control_plan.md` §5 for test set integrity controls.

## 2. Data Collection Protocol

{{DATA_COLLECTION_DESCRIPTION}}

- Imaging modality / acquisition protocol: {{MODALITY}}
- Site(s): {{SITES}}
- Inclusion criteria: {{INCLUSION_CRITERIA}}
- Exclusion criteria: {{EXCLUSION_CRITERIA}}
- Labeling procedure: {{LABELING_PROCEDURE}}
- Label quality assurance: {{QA_PROCEDURE}}

## 3. Patient Demographics

| Characteristic | Training Set | Test Set |
|---|---|---|
| Age (mean ± SD) | {{AGE_TRAIN}} | {{AGE_TEST}} |
| Sex (% female) | {{SEX_TRAIN}} | {{SEX_TEST}} |
| {{DEMOGRAPHIC_1}} | {{VALUE_TRAIN}} | {{VALUE_TEST}} |
| {{DEMOGRAPHIC_2}} | {{VALUE_TRAIN}} | {{VALUE_TEST}} |

## 4. Known Limitations and Gaps

| Limitation | Description | Mitigating Control |
|---|---|---|
| {{LIMITATION_1}} | {{DESCRIPTION}} | {{MITIGATION}} |
| Underrepresented subgroups | {{GROUPS}} are underrepresented relative to the intended patient population | Contraindication in labeling; flag in intended use statement |

## 5. Bias Assessment

Bias was evaluated across the following subgroups:

| Subgroup | N (test) | {{METRIC}} | Difference from Overall | Acceptable? |
|---|---|---|---|---|
| {{SUBGROUP_1}} | {{N}} | {{VALUE}} | {{DIFF}} | {{YES_NO}} |
| {{SUBGROUP_2}} | {{N}} | {{VALUE}} | {{DIFF}} | {{YES_NO}} |

Subgroups where performance difference exceeds {{THRESHOLD}} relative to overall performance
are flagged and addressed via:
- Contraindication in labeling, or
- Targeted data augmentation in retraining, or
- Explicit risk control in `04_risk_management/risk_control_measures.md`

## 6. Data Integrity Controls

- All datasets are stored with SHA-256 hashes recorded below.
- Datasets are read-only after the freeze date.
- Access is controlled via {{ACCESS_CONTROL_METHOD}}.

| Dataset | Freeze Date | SHA-256 | Location |
|---|---|---|---|
| {{DATASET_1}} | {{DATE}} | {{HASH}} | {{PATH}} |
| {{DATASET_2}} | {{DATE}} | {{HASH}} | {{PATH}} |
| {{DATASET_3}} | {{DATE}} | {{HASH}} | {{PATH}} |
