# DHF Template Completion Checklist

Complete these sections in order before submission. See [explanation.md](explanation.md)
for the full document map including standard clause references and auto-population sources.

Sections marked **[AUTO]** can be mostly filled by scripts from `requirements.yaml`,
`soup.yaml`, `git log`, or CI artifacts.

## Phase 1 — Device Identity and Development Plan
- [ ] `10_software_development_plan/sdp.md` — lifecycle model, tools, standards, personnel roles
- [ ] `01_device_description/intended_use.md` — intended use, patient population, indications, contraindications
- [ ] `01_device_description/software_classification.md` — determine IEC 62304 Class (A/B/C), document rationale
- [ ] `05_soup/soup_register.md` **[AUTO from soup.yaml]** — list all direct and transitive SOUP with versions and licenses

## Phase 2 — Requirements and Architecture
- [ ] `02_requirements/system_requirements.md` **[AUTO from requirements.yaml]** — domain count table, link to requirements.yaml
- [ ] `02_requirements/traceability_index.md` **[AUTO from traceability_matrix.md]** — link to generated matrices, coverage stats
- [ ] `03_architecture/software_architecture.md` — component boundaries and data flow
- [ ] `03_architecture/interfaces.md` — key data contracts and error types

## Phase 3 — Risk Management
- [ ] `04_risk_management/risk_management_plan.md` — scope, responsibilities, review schedule
- [ ] `04_risk_management/hazard_analysis.md` — hazard/harm/severity/probability table for each RSK requirement
- [ ] `04_risk_management/risk_control_measures.md` **[PARTIAL: RSK IDs from requirements.yaml]** — RSK-ID → control measure mapping
- [ ] `04_risk_management/residual_risk_evaluation.md` **[PARTIAL: RSK IDs auto]** — confirm residual risk is acceptable

## Phase 4 — SOUP Risk and Verification
- [ ] `05_soup/soup_risk_analysis.md` **[PARTIAL: packages from soup.yaml]** — failure mode analysis per SOUP item
- [ ] `05_soup/soup_monitoring_plan.md` — already mostly boilerplate; confirm CVE response SLAs
- [ ] `06_verification/verification_plan.md` — verification activities per IEC 62304 §8
- [ ] `06_verification/evidence_index.md` **[AUTO from artifacts/evidence_runs/]** — link to EvidenceReport JSON artifacts from CI

## Phase 5 — Configuration Management and Tool Validation
- [ ] `07_configuration_management/cm_plan.md` — branching strategy, release tagging policy
- [ ] `07_configuration_management/baseline_register.md` **[AUTO from git tags]** — capture all repo SHAs at each release
- [ ] `12_tool_validation/tool_validation.md` — qualify all development and verification tools

## Phase 6 — Security and Change Control
- [ ] `08_security/threat_model.md` — data flows, trust boundaries, STRIDE threats
- [ ] `08_security/vulnerability_response.md` — CVE response timeline and escalation
- [ ] `08_security/security_assessment.md` — confirm CodeQL, pip-audit, Dependabot are active
- [ ] `09_change_control/change_control_procedure.md` — PR policy, required approvals, impact assessment
- [ ] `09_change_control/change_log.md` **[AUTO from git log]** — complete change history

## Phase 7 — AI/ML Documents (if applicable)
- [ ] `13_ai_ml/training_data_description.md` — dataset provenance, demographics, bias assessment
- [ ] `13_ai_ml/predetermined_change_control_plan.md` — algorithm change protocol, performance bounds
- [ ] `13_ai_ml/model_performance_monitoring_plan.md` — drift thresholds, retraining triggers

## Phase 8 — Usability and Maintenance
- [ ] `15_usability/usability_engineering_plan.md` — use context, user tasks, use errors, summative testing
- [ ] `14_maintenance_plan/software_maintenance_plan.md` — monitoring cadence, support lifecycle, EOL policy

## Phase 9 — Anomaly Log (ongoing)
- [ ] `11_anomaly_log/anomaly_log.md` — open at project start; maintain continuously; review before release

## Context-Dependent Sections

Create these only if they apply to your regulatory pathway:

- [ ] `16_predicate/` — 510(k) pathway: predicate device selection and substantial equivalence table
- [ ] `17_labeling/` — all pathways: IFU, warnings, contraindications in labeling format
- [ ] `18_clinical_evaluation/` — EU MDR / De Novo: literature review and clinical evidence summary
- [ ] `19_post_market/` — EU MDR: post-market surveillance plan and PMCF
