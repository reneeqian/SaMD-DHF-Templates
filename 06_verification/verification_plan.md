# Verification Plan — {{PROJECT_NAME}}

## Scope

Verification activities per IEC 62304 §8 for {{PROJECT_NAME}}.

## Verification Approach

| Level | Method | Tooling |
|-------|--------|---------|
| Unit | Automated pytest | pytest + coverage.py |
| Integration | Automated pytest | pytest |
| System | Smoke tests on real data | Manual / scripted |
| Risk control verification | Automated pytest (RSK tests) | pytest |

## Verification Entry Points

```bash
cd {{CODE_REPO}} && python runtests.py   # runs tests + generates traceability matrix + forge health
```

## Evidence Generation

Each test decorated with `@pytest.mark.requirement("DOMAIN-NNN")` generates an
`EvidenceReport` JSON artifact saved to `artifacts/evidence_runs/`. These are uploaded
as CI artifacts and indexed in `06_verification/evidence_index.md`.

## Acceptance Criteria

| Metric | Threshold |
|--------|-----------|
| Test pass rate | 100% |
| Requirements coverage | 100% |
| forge health grade | ≥ B |
| pip-audit CVEs | 0 (high or critical) |
