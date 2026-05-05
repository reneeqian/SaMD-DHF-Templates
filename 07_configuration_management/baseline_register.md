# Baseline Register — {{PROJECT_NAME}}

Records the exact Git SHAs of all component repositories at each release.

## Release Baselines

| Release | Date | {{REPO_1}} SHA | {{REPO_2}} SHA | Notes |
|---------|------|---------------|---------------|-------|
| v0.1.0 | {{DATE}} | {{SHA}} | {{SHA}} | Initial baseline |

## How to Record a Baseline

```bash
git -C /path/to/repo rev-parse HEAD
```

Add the SHA to the table above. All SHAs must correspond to tagged commits.
