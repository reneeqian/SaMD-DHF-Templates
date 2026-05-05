# Threat Model — {{PROJECT_NAME}}

## Data Flows

{{DATA_FLOW_DIAGRAM}}

## Trust Boundaries

| Boundary | Description |
|----------|-------------|
| {{BOUNDARY_1}} | {{DESCRIPTION_1}} |

## Threat Table (STRIDE)

| ID | Threat Category | Asset | Threat | Mitigation |
|----|----------------|-------|--------|-----------|
| T-001 | Tampering | Model artifact | Corrupted model file used for inference | Manifest integrity check (RSK-002) |
| T-002 | Information Disclosure | Patient data | Unauthorized data access | {{MITIGATION}} |

## Out of Scope

{{OUT_OF_SCOPE}}
