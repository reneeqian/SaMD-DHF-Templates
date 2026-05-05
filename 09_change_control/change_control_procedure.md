# Change Control Procedure — {{PROJECT_NAME}}

## Change Categories

| Category | Examples | Required Review |
|----------|---------|----------------|
| Minor | Typo fixes, documentation only | Single approver |
| Moderate | Non-safety code changes, new features | Single approver + CI |
| Major | Safety-critical changes, risk control modifications | Two approvers + risk assessment |

## Change Process

1. Create feature branch from `dev`
2. Implement changes with requirement traceability (`@pytest.mark.requirement`)
3. Run `python runtests.py` — must pass at Grade ≥ B with 100% requirements coverage
4. Open PR targeting `dev`; describe change category and impact
5. Obtain required approvals per category above
6. After merge to `dev`: open `dev → main` PR for release

## Change Impact Assessment

For any change to risk control requirements (RSK-NNN):
- Update `04_risk_management/risk_control_measures.md`
- Re-evaluate `04_risk_management/residual_risk_evaluation.md`
- Update `09_change_control/change_log.md`
