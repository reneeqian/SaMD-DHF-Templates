# DHF Template Explanation Guide

This document explains every file in this repository: what it is, what goes in it, which
regulatory clause requires it, how often to update it, and how it maps to an FDA submission.

---

## Section 1 — Document Map

| Section | File | Purpose | What Goes In It | Standard Clause | Update Frequency |
|---|---|---|---|---|---|
| 01 | [intended_use.md](01_device_description/intended_use.md) | Defines the device's clinical role and regulatory scope | Intended use statement, patient population, indications, contraindications, operating environment | IEC 62304 §5.1.1; FDA 21 CFR 807.87(e) | Once at project start; update if scope changes |
| 01 | [software_classification.md](01_device_description/software_classification.md) | Establishes IEC 62304 Class A/B/C and FDA risk class | Three-criterion hazard table, resulting class, FDA class, regulatory pathway | IEC 62304 §4.3; ISO 14971 §4.1 | Once; re-evaluate at major feature additions |
| 02 | [system_requirements.md](02_requirements/system_requirements.md) | Links the DHF to machine-readable requirements | Domain count table, pointer to `requirements.yaml` in each code repo | IEC 62304 §5.2 | Every sprint when requirements are added |
| 02 | [traceability_index.md](02_requirements/traceability_index.md) | Proves every requirement is verified | Links to generated `traceability_matrix.md`, coverage statistics per repo | IEC 62304 §5.5.5, §8.1.3 | Every CI run (auto-populated) |
| 03 | [software_architecture.md](03_architecture/software_architecture.md) | Describes system decomposition and data flow | Component diagram, component table, data flow narrative, key design decisions | IEC 62304 §5.3 | When architecture changes |
| 03 | [interfaces.md](03_architecture/interfaces.md) | Documents data contracts at system boundaries | Interface table, API boundaries, error type taxonomy | IEC 62304 §5.3.5 | When interfaces change |
| 04 | [risk_management_plan.md](04_risk_management/risk_management_plan.md) | Defines the risk management process | Scope, roles and responsibilities, risk acceptability criteria, review schedule | ISO 14971 §4 | Once; update at major releases |
| 04 | [hazard_analysis.md](04_risk_management/hazard_analysis.md) | Identifies foreseeable hazards and harms | Hazard table: hazard → harm → severity → probability → risk level → RSK requirement | ISO 14971 §5–6; IEC 62304 §4.2 | When new hazards are identified |
| 04 | [risk_control_measures.md](04_risk_management/risk_control_measures.md) | Maps RSK requirements to hazard controls | RSK ID → control measure → implementation location → verification test | ISO 14971 §6 | When RSK requirements are added or changed |
| 04 | [residual_risk_evaluation.md](04_risk_management/residual_risk_evaluation.md) | Confirms benefit outweighs residual risk | Residual risk table, overall conclusion, reviewer signature | ISO 14971 §7 | Each major release |
| 05 | [soup_register.md](05_soup/soup_register.md) | Inventories all SOUP with exact versions | Direct + transitive package table with role, license, CVE tool, last audit date | IEC 62304 §8.1 | Every dependency change (auto-populated from soup.yaml) |
| 05 | [soup_risk_analysis.md](05_soup/soup_risk_analysis.md) | Characterizes failure modes for each SOUP item | Package → potential failure mode → severity → mitigation | IEC 62304 §8.1.2 | Every dependency change |
| 05 | [soup_monitoring_plan.md](05_soup/soup_monitoring_plan.md) | Describes ongoing SOUP surveillance process | CVE scan cadence, Dependabot policy, response SLA, version drift handling | IEC 62304 §8.1.3 | Once; review annually |
| 06 | [verification_plan.md](06_verification/verification_plan.md) | Defines how verification activities are conducted | Test levels, tooling, entry points, acceptance criteria | IEC 62304 §5.5, §8 | Once; update if tooling changes |
| 06 | [evidence_index.md](06_verification/evidence_index.md) | Indexes all verification evidence artifacts | CI run links, test pass rate, coverage %, forge grade per repo | IEC 62304 §5.5.6 | Every CI run (auto-populated from artifacts/) |
| 07 | [cm_plan.md](07_configuration_management/cm_plan.md) | Defines the configuration management process | Branching strategy, release tagging policy, tool qualification reference | IEC 62304 §5.1.4, §8.3 | Once; update if branching strategy changes |
| 07 | [baseline_register.md](07_configuration_management/baseline_register.md) | Records exact Git SHAs at each release | Per-repo SHA table indexed by version tag | IEC 62304 §8.3.1 | Each release (auto-populated from git tags) |
| 08 | [threat_model.md](08_security/threat_model.md) | Identifies cybersecurity threats and mitigations | Data flow diagram, trust boundaries, STRIDE threat table | FDA Cybersecurity Guidance (2023); IEC 81001-5-1 | When data flows or deployment changes |
| 08 | [vulnerability_response.md](08_security/vulnerability_response.md) | Documents the CVE response process | Response timeline by severity, remediation steps, escalation path | FDA Cybersecurity Guidance; IEC 62304 §9 | Once; review annually |
| 08 | [security_assessment.md](08_security/security_assessment.md) | Summarizes active security controls | Static analysis, dependency scanning, Dependabot status table | FDA Cybersecurity Guidance | Each major release |
| 09 | [change_control_procedure.md](09_change_control/change_control_procedure.md) | Defines the PR and change review process | Change categories, required approvals, risk impact assessment steps | IEC 62304 §6.2 | Once; update if review policy changes |
| 09 | [change_log.md](09_change_control/change_log.md) | Records every change with risk impact | Version, date, category, description, risk impact, author | IEC 62304 §8.2.4 | Each release (auto-populated from git log) |
| 10 | [sdp.md](10_software_development_plan/sdp.md) | Software development plan | Lifecycle model, development tools, applicable standards, personnel roles | IEC 62304 §5.1 | Once at project start; update if tools or roles change |
| 11 | [anomaly_log.md](11_anomaly_log/anomaly_log.md) | Formal problem resolution record | Anomaly ID, discovery date, severity, description, status, resolution, linked PR | IEC 62304 §9 | Continuously — every defect or anomaly |
| 12 | [tool_validation.md](12_tool_validation/tool_validation.md) | Tool qualification records | Per-tool: name, version, validation method, qualification rationale, acceptance criteria | FDA 21 CFR 820.70(i) | When a new tool is introduced or upgraded |
| 13 | [predetermined_change_control_plan.md](13_ai_ml/predetermined_change_control_plan.md) | Algorithm change protocol for adaptive AI/ML | Change types, pre-specified performance bounds, update decision criteria | FDA AI/ML SaMD Guidance (2021) §V | When algorithm change categories are defined |
| 13 | [training_data_description.md](13_ai_ml/training_data_description.md) | Training dataset provenance and bias assessment | Dataset sources, demographics, inclusion/exclusion criteria, known limitations, bias evaluation | FDA AI/ML SaMD Guidance §III | When training data is updated or retraining occurs |
| 13 | [model_performance_monitoring_plan.md](13_ai_ml/model_performance_monitoring_plan.md) | Post-market model performance monitoring | Performance metrics, drift thresholds, retraining triggers, reporting cadence | FDA AI/ML SaMD Guidance §VI | When monitoring thresholds are revised |
| 14 | [software_maintenance_plan.md](14_maintenance_plan/software_maintenance_plan.md) | Post-release software maintenance | Monitoring activities, support lifecycle, end-of-life policy, maintenance change process | IEC 62304 §6.1 | Once at first release; review annually |
| 15 | [usability_engineering_plan.md](15_usability/usability_engineering_plan.md) | Human factors and usability engineering process | Use context, user tasks, known use errors, formative and summative testing approach | IEC 62366 §5 | Once; update if user tasks or environment changes |

---

## Section 2 — Auto-Population Reference

Documents marked **Auto** can be mostly filled by scripts from machine-readable project files.
Documents marked **Manual** require regulatory judgment that no script can replace.

| File | Auto-Population Source | Level |
|---|---|---|
| `02_requirements/system_requirements.md` | `docs/requirements.yaml` — count `id:` entries per domain prefix | Auto |
| `02_requirements/traceability_index.md` | `docs/traceability_matrix.md` — parse coverage stats | Auto |
| `05_soup/soup_register.md` | `docs/soup.yaml` — render as markdown table | Auto |
| `05_soup/soup_risk_analysis.md` | `docs/soup.yaml` — package names only; failure modes are manual | Partial |
| `06_verification/evidence_index.md` | `artifacts/evidence_runs/` + CI run metadata | Auto |
| `07_configuration_management/baseline_register.md` | `git tag -l` + `git rev-parse <tag>` | Auto |
| `09_change_control/change_log.md` | `git log` + `pyproject.toml` version | Auto |
| `04_risk_management/risk_control_measures.md` | RSK-* IDs from `requirements.yaml`; measure text is manual | Partial |
| `04_risk_management/residual_risk_evaluation.md` | RSK-* IDs from `requirements.yaml`; risk judgment is manual | Partial |
| `01_device_description/intended_use.md` | No machine source — clinical scope is always manual | Manual |
| `01_device_description/software_classification.md` | No machine source — Class A/B/C is a risk judgment | Manual |
| `03_architecture/software_architecture.md` | No machine source — diagrams and design rationale | Manual |
| `04_risk_management/hazard_analysis.md` | No machine source — hazard identification requires domain expertise | Manual |
| `08_security/threat_model.md` | No machine source — data flow and trust boundary analysis | Manual |

---

## Section 3 — DHF → FDA 510(k) Submission Mapping

The FDA expects a complete software documentation package as part of a 510(k) or De Novo
submission. The table below shows which FDA-required sections are satisfied by which DHF files,
and how much of each section can be auto-populated.

For **Moderate** and **Major** level of concern software, all rows apply. For **Minor** level
of concern, rows marked † are required; others are strongly recommended.

| FDA 510(k) Required Section | Satisfied By (DHF Files) | Auto-Populated? |
|---|---|---|
| † Device Description | `01_device_description/intended_use.md` | No — manual |
| † Software Level of Concern | `01_device_description/software_classification.md` | No — manual |
| Substantial Equivalence / Predicate Comparison | `16_predicate/` *(template not yet created)* | No |
| † Software Description | `03_architecture/software_architecture.md` | Partial |
| † Software Requirements Specification | `02_requirements/system_requirements.md` + `docs/requirements.yaml` | Yes — link to YAML |
| Architecture Design Chart | `03_architecture/software_architecture.md` | No — diagram required |
| Software Design Specification | `03_architecture/interfaces.md` | Partial |
| † Traceability Analysis | `02_requirements/traceability_index.md` + per-repo `traceability_matrix.md` | Yes — auto-generated |
| Software Development Environment | `10_software_development_plan/sdp.md` | Partial |
| Software Development and Maintenance Practices | `10_software_development_plan/sdp.md` + `07_configuration_management/cm_plan.md` | Partial |
| † Verification and Validation Summary | `06_verification/verification_plan.md` + `evidence_index.md` | Partial — evidence auto |
| † Revision Level History | `09_change_control/change_log.md` + `07_configuration_management/baseline_register.md` | Yes |
| † Unresolved Anomalies | `11_anomaly_log/anomaly_log.md` | Partial — requires manual triage |
| Hazard Analysis / Risk Management | `04_risk_management/` (all four files) | Partial |
| SOUP Software List | `05_soup/soup_register.md` | Yes — from `soup.yaml` |
| Cybersecurity Documentation | `08_security/` (all three files) | Partial |

† = Required for all levels of concern (Minor, Moderate, Major).

### Additional Requirements by Pathway

**De Novo submission** additionally requires:
- Clinical performance data demonstrating safety and effectiveness
- Proposed special controls
- Labeling (`17_labeling/` — template not yet created)

**EU MDR / IVDR Technical File** additionally requires:
- Clinical evaluation report (`18_clinical_evaluation/` — template not yet created)
- Post-market surveillance plan (`19_post_market/` — template not yet created)
- Declaration of Conformity (device-specific, not templatizable)
- Summary of Safety and Clinical Performance (SSCP) for Class IIb/III implantables

**FDA AI/ML SaMD** additionally requires:
- Predetermined Change Control Plan / Algorithm Change Protocol (`13_ai_ml/predetermined_change_control_plan.md`)
- Description of training data (`13_ai_ml/training_data_description.md`)
- Performance monitoring plan (`13_ai_ml/model_performance_monitoring_plan.md`)

---

## Section 4 — What Will Always Require Manual Work

No script or template auto-fill can replace these. They require regulatory judgment,
clinical domain expertise, or a qualified signature:

- **Intended use and indications** — defines regulatory scope; errors here affect the entire submission
- **IEC 62304 Class A/B/C determination** — drives the entire documentation burden
- **Hazard identification and risk scoring** — requires domain knowledge of failure modes and clinical harm
- **Residual risk acceptability conclusion** — qualitative judgment that benefit outweighs risk
- **Architecture diagrams** — must reflect actual deployed system topology
- **Data flow and trust boundary diagrams** (threat model) — must reflect real deployment
- **Predicate device selection** (510(k)) — strategic regulatory decision
- **Clinical evaluation** (EU MDR / De Novo) — requires literature review and clinical expertise
- **Any document requiring a reviewer signature or date** — must be signed by a named responsible person
