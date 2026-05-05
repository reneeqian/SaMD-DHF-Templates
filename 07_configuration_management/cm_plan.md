# Configuration Management Plan — {{PROJECT_NAME}}

## Branching Strategy

- `main` — stable releases only; PRs required with at least 1 approving review
- `dev` — integration branch; direct pushes permitted
- Feature branches — created from `dev`, merged via PR

## Release Tagging Policy

1. Increment `version` in `pyproject.toml` (semantic versioning)
2. Tag release: `git tag -a vX.Y.Z -m "Release vX.Y.Z"`
3. Push tag: `git push origin vX.Y.Z`
4. Create GitHub release with release notes
5. Update `07_configuration_management/baseline_register.md` with new SHA
6. Update SOUP consumers to pin `@vX.Y.Z`

## Baseline Register

See [baseline_register.md](baseline_register.md).

## Tool Qualification

Software tools used in the development or verification of this device shall be
qualified per FDA 21 CFR Part 820.70(i) and IEC 62304 §5.1.4. See
`10_tool_validation/` for tool validation records.
