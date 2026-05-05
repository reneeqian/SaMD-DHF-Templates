# SOUP Risk Analysis — {{PROJECT_NAME}}

## Analysis per IEC 62304 §8.1.2

For each SOUP item, describe potential failure modes and mitigations.

| Package | Potential Failure Mode | Severity | Mitigation |
|---------|----------------------|----------|-----------|
| {{PACKAGE}} | {{FAILURE_MODE}} | {{SEVERITY}} | {{MITIGATION}} |

## General Mitigations Applied

- All SOUP dependencies are pinned to exact versions in `pyproject.toml` and `docs/soup.yaml`.
- Automated CVE scanning via `pip-audit` runs on every push and weekly schedule.
- CycloneDX SBOM generated per CI run.
- Dependabot configured for automated vulnerability alerts.
