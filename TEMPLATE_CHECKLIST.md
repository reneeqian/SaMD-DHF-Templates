# DHF Template Completion Checklist

Complete these sections in order before submission.

## Phase 1 — Device Identity
- [ ] `01_device_description/intended_use.md` — fill intended use, patient population, indications, contraindications
- [ ] `01_device_description/software_classification.md` — determine IEC 62304 Class (A/B/C), document rationale
- [ ] `05_soup/soup_register.md` — list all direct and transitive SOUP with versions and licenses

## Phase 2 — Requirements and Architecture
- [ ] `02_requirements/system_requirements.md` — document or link to requirements.yaml
- [ ] `02_requirements/traceability_index.md` — link to generated traceability_matrix.md in each code repo
- [ ] `03_architecture/software_architecture.md` — describe component boundaries and data flow
- [ ] `03_architecture/interfaces.md` — document key data contracts

## Phase 3 — Risk Management
- [ ] `04_risk_management/risk_management_plan.md` — scope, responsibilities, review schedule
- [ ] `04_risk_management/hazard_analysis.md` — hazard/harm/severity/probability table for each RSK requirement
- [ ] `04_risk_management/risk_control_measures.md` — RSK-ID → control measure mapping
- [ ] `04_risk_management/residual_risk_evaluation.md` — confirm residual risk is acceptable

## Phase 4 — Verification
- [ ] `06_verification/verification_plan.md` — verification activities per IEC 62304 §8
- [ ] `06_verification/evidence_index.md` — link to EvidenceReport JSON artifacts from CI

## Phase 5 — Configuration Management
- [ ] `07_configuration_management/cm_plan.md` — branching strategy, release tagging policy
- [ ] `07_configuration_management/baseline_register.md` — capture all repo SHAs at each release

## Phase 6 — Security and Change Control
- [ ] `08_security/threat_model.md` — data flows, trust boundaries, threats
- [ ] `08_security/vulnerability_response.md` — CVE response timeline and escalation
- [ ] `09_change_control/change_control_procedure.md` — PR policy, required approvals
