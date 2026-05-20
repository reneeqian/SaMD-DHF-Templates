# SaMD Design History File (DHF) Templates

Reusable scaffold for IEC 62304 / ISO 14971 / IEC 62366 / FDA AI-ML SaMD projects.

See [explanation.md](explanation.md) for a full document map: what each file is,
what goes in it, which standard clause it satisfies, and how it maps to an FDA submission.

## How to Use

1. Use this repository as a GitHub Template (click **Use this template** → **Create a new repository**)
2. Replace all `{{PROJECT_NAME}}`, `{{IEC_62304_CLASS}}`, `{{DEVICE_DESCRIPTION}}` placeholders
3. Fill sections in the order shown in [TEMPLATE_CHECKLIST.md](TEMPLATE_CHECKLIST.md)
4. Link traceability artifacts from your code repositories to `02_requirements/traceability_index.md`
5. Update `05_soup/soup_register.md` whenever a dependency is added or upgraded

Several sections can be auto-populated from machine-readable project files
(`docs/requirements.yaml`, `docs/soup.yaml`, `git` history). See
[explanation.md §2](explanation.md#section-2--auto-population-reference) for details.

## Repository Structure

```
explanation.md               — document map, auto-population guide, FDA submission mapping

01_device_description/       — intended use, software classification
02_requirements/             — system requirements and traceability index
03_architecture/             — software architecture and interfaces
04_risk_management/          — ISO 14971 hazard analysis and risk controls
05_soup/                     — SOUP register, risk analysis, monitoring plan
06_verification/             — verification plan and evidence index
07_configuration_management/ — CM plan and baseline register
08_security/                 — threat model and vulnerability response
09_change_control/           — change control procedure and log
10_software_development_plan/ — IEC 62304 §5.1 software development plan
11_anomaly_log/              — IEC 62304 §9 problem resolution record
12_tool_validation/          — FDA 21 CFR 820.70(i) tool qualification records
13_ai_ml/                    — FDA AI/ML SaMD: PCCP, training data, monitoring plan
14_maintenance_plan/         — IEC 62304 §6.1 post-release maintenance plan
15_usability/                — IEC 62366 usability engineering plan
```

Context-dependent sections (create if applicable to your regulatory pathway):
```
16_predicate/                — 510(k) substantial equivalence analysis
17_labeling/                 — IFU and device labeling
18_clinical_evaluation/      — EU MDR clinical evaluation report
19_post_market/              — EU MDR post-market surveillance plan
```

## Regulatory References

- IEC 62304:2006+AMD1:2015 — Medical device software lifecycle processes
- ISO 14971:2019 — Risk management for medical devices
- IEC 62366-1:2015 — Usability engineering for medical devices
- FDA Guidance: Artificial Intelligence and Machine Learning in Software as a Medical Device (2021)
- FDA Guidance: Cybersecurity in Medical Devices (2023)
- FDA 21 CFR Part 820.70(i) — Production and process controls (software tools)
