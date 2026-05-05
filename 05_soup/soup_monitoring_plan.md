# SOUP Monitoring Plan — {{PROJECT_NAME}}

## Monitoring Activities

| Activity | Frequency | Responsible | Tool |
|----------|-----------|-------------|------|
| CVE scan | Every push + weekly | CI | pip-audit |
| Dependabot alerts | Continuous | GitHub | Dependabot |
| SBOM generation | Every CI run | CI | pip-audit --format cyclonedx-json |
| SOUP version review | Each major release | Developer | Manual + pip-audit |

## Response to Identified Vulnerabilities

1. **Critical/High CVE in direct SOUP:** Upgrade within 30 days or implement compensating control.
2. **Medium CVE in direct SOUP:** Evaluate within 90 days; document risk acceptance if not upgraded.
3. **Low CVE:** Document in change log; address in next planned release.
4. **CVE in transitive SOUP only:** Upgrade direct dep if feasible; otherwise document.

## SOUP Version Drift

soup_checker in `regulatory_tools` validates that `docs/soup.yaml` versions match installed
versions. Drift is treated as a CI failure.
