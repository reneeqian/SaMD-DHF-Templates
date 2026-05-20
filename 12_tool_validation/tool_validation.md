# Tool Validation Records — {{PROJECT_NAME}}

Software tools used in the development or verification of a medical device must be
qualified per FDA 21 CFR Part 820.70(i) and IEC 62304 §5.1.4.

The required level of validation scales with how the tool is used:
- **Category 1 — Infrastructure tools** (git, GitHub Actions): no formal qualification needed; the tool's output is independently verifiable by the developer.
- **Category 2 — Verification tools** (pytest, coverage.py, ruff, mypy): qualification required — demonstrate the tool correctly identifies the defect class it is intended to find.
- **Category 3 — Safety-critical tools** (tools that directly produce outputs influencing clinical decisions): full IQ/OQ/PQ qualification required.

## Qualification Records

---

### pytest — Test Execution Framework

| Field | Value |
|---|---|
| Tool name | pytest |
| Version | {{PYTEST_VERSION}} |
| Category | Category 2 — Verification tool |
| Intended use | Execute unit and integration tests; report pass/fail results |
| Qualification method | Execute a known-failing test; confirm pytest reports failure. Execute a known-passing test; confirm pytest reports pass. |
| Acceptance criteria | pytest exit code 1 on failure; exit code 0 on all-pass. Output matches expected test count. |
| Date qualified | {{DATE}} |
| Qualified by | {{NAME}} |

---

### coverage.py — Code Coverage Measurement

| Field | Value |
|---|---|
| Tool name | coverage.py |
| Version | {{COVERAGE_VERSION}} |
| Category | Category 2 — Verification tool |
| Intended use | Measure line and branch coverage of test suite; report coverage percentage |
| Qualification method | Write a module with two branches; cover only one; confirm coverage.py reports < 100%. Cover both; confirm 100%. |
| Acceptance criteria | Coverage report correctly identifies uncovered lines; percentage matches manual count. |
| Date qualified | {{DATE}} |
| Qualified by | {{NAME}} |

---

### ruff — Static Analysis and Linting

| Field | Value |
|---|---|
| Tool name | ruff |
| Version | {{RUFF_VERSION}} |
| Category | Category 2 — Verification tool |
| Intended use | Detect code style violations, potential errors, and security anti-patterns |
| Qualification method | Introduce a known lint violation (e.g., unused import); confirm ruff flags it. Fix the violation; confirm ruff exits clean. |
| Acceptance criteria | ruff exit code 1 when violations present; exit code 0 when clean. |
| Date qualified | {{DATE}} |
| Qualified by | {{NAME}} |

---

### mypy — Static Type Checker

| Field | Value |
|---|---|
| Tool name | mypy |
| Version | {{MYPY_VERSION}} |
| Category | Category 2 — Verification tool |
| Intended use | Detect type errors in Python source before runtime |
| Qualification method | Introduce a known type error (wrong argument type); confirm mypy flags it. Fix the error; confirm mypy exits clean. |
| Acceptance criteria | mypy reports error on known type violation; exits 0 when clean. |
| Date qualified | {{DATE}} |
| Qualified by | {{NAME}} |

---

### pip-audit — SOUP Vulnerability Scanner

| Field | Value |
|---|---|
| Tool name | pip-audit |
| Version | {{PIP_AUDIT_VERSION}} |
| Category | Category 2 — Verification tool |
| Intended use | Identify known CVEs in installed Python packages against OSV and PyPI advisory databases |
| Qualification method | Install a package with a known historical CVE in an isolated environment; confirm pip-audit reports it. |
| Acceptance criteria | pip-audit identifies the known CVE; exit code 1 when vulnerabilities found; exit code 0 when clean. |
| Date qualified | {{DATE}} |
| Qualified by | {{NAME}} |

---

### forge-utils — Health Grading and Traceability

| Field | Value |
|---|---|
| Tool name | forge-utils (`forge`) |
| Version | {{FORGE_VERSION}} |
| Category | Category 2 — Verification tool |
| Intended use | Aggregate collector scores into a project health grade; generate traceability matrix |
| Qualification method | Run `forge health` on a project with known coverage and requirements state; confirm grade and matrix match expected values. |
| Acceptance criteria | Grade matches manual calculation from collector scores; traceability matrix lists all `@pytest.mark.requirement` markers. |
| Date qualified | {{DATE}} |
| Qualified by | {{NAME}} |

---

### git — Version Control

| Field | Value |
|---|---|
| Tool name | git |
| Version | {{GIT_VERSION}} |
| Category | Category 1 — Infrastructure tool |
| Intended use | Track source code changes; maintain branch and tag history |
| Qualification method | Qualification not required. Commit contents are independently verifiable by any developer via `git log` and `git diff`. |
| Acceptance criteria | N/A |
| Notes | GitHub enforces branch protection rules (require PR, no force-push to main) as a compensating control. |

---

## Re-qualification Policy

Tools must be re-qualified when:
- The major or minor version changes (e.g., 1.x → 2.x or 1.2 → 1.3)
- A CVE affecting the tool's qualification-relevant behavior is patched
- The tool is used in a new context beyond its original intended use

Minor patch upgrades (e.g., 1.2.3 → 1.2.4) for bug fixes only: document the upgrade in
`09_change_control/change_log.md`; re-qualification may be deferred unless the change
affects the tool's core behavior.
