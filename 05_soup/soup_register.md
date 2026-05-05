# SOUP Register — {{PROJECT_NAME}}

## Direct SOUP

Packages directly declared in medical device code repositories.

| Package | Version | Repo(s) | Role | License | CVE Check | Last Audited |
|---------|---------|---------|------|---------|-----------|--------------|
| {{PACKAGE}} | {{VERSION}} | {{REPOS}} | {{ROLE}} | {{LICENSE}} | pip-audit | — |

## Transitive SOUP

Packages introduced indirectly via direct SOUP (e.g., via forge-utils).

| Package | Version | Via | Role | License |
|---------|---------|-----|------|---------|
| {{PACKAGE}} | {{VERSION}} | {{VIA}} | {{ROLE}} | {{LICENSE}} |

## Notes

- CVE checking is automated via `pip-audit` in CI for all code repositories.
- CycloneDX SBOM artifacts are generated per CI run and available as workflow artifacts.
- SOUP versions shall be reviewed and updated at each major release.
- Versions marked `runtime` are unauditable and must be pinned before submission.
