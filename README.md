# SaMD Design History File (DHF) Templates

Reusable scaffold for IEC 62304 / ISO 14971 / FDA AI-ML SaMD projects.

## How to Use

1. Use this repository as a GitHub Template (click **Use this template** → **Create a new repository**)
2. Replace all `{{PROJECT_NAME}}`, `{{IEC_62304_CLASS}}`, `{{DEVICE_DESCRIPTION}}` placeholders
3. Fill sections in the order shown in [TEMPLATE_CHECKLIST.md](TEMPLATE_CHECKLIST.md)
4. Link traceability artifacts from your code repositories to `02_requirements/traceability_index.md`
5. Update `05_soup/soup_register.md` whenever a dependency is added or upgraded

## Repository Structure

```
01_device_description/    — intended use, software classification
02_requirements/          — system requirements and traceability index
03_architecture/          — software architecture and interfaces
04_risk_management/       — ISO 14971 hazard analysis and risk controls
05_soup/                  — SOUP register, risk analysis, monitoring plan
06_verification/          — verification plan and evidence index
07_configuration_management/ — CM plan and baseline register
08_security/              — threat model and vulnerability response
09_change_control/        — change control procedure and log
```

## Regulatory References

- IEC 62304:2006+AMD1:2015 — Medical device software lifecycle processes
- ISO 14971:2019 — Risk management for medical devices
- FDA Guidance: Artificial Intelligence and Machine Learning in Software as a Medical Device (2021)
- FDA 21 CFR Part 820.70(i) — Production and process controls (software tools)
