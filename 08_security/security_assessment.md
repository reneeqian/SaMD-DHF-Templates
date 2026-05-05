# Security Assessment — {{PROJECT_NAME}}

## Static Analysis

CodeQL runs on every push and PR (see `.github/workflows/codeql.yml` in code repos).
Results are available in the GitHub Security tab.

## Dependency Vulnerability Scanning

`pip-audit` runs on every push and PR. Dependabot provides continuous monitoring.
High and critical CVEs are blocking via branch protection rules.

## Assessment Summary

| Control | Status | Notes |
|---------|--------|-------|
| Static analysis (CodeQL) | Active | {{STATUS}} |
| Dependency scanning (pip-audit) | Active | {{STATUS}} |
| Automated CVE monitoring (Dependabot) | Active | {{STATUS}} |
| GPL/AGPL license blocking | Active | dependency-review.yml |
