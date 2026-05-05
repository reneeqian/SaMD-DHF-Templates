# Software Classification — {{PROJECT_NAME}}

## IEC 62304 Classification: {{IEC_62304_CLASS}}

### Decision Rationale

| Criterion | Assessment |
|-----------|-----------|
| Serious injury possible if software fails? | {{YES_NO}} |
| Injury mitigated by operator or other means? | {{YES_NO}} |
| Death possible if software fails? | {{YES_NO}} |

**Resulting class:** {{IEC_62304_CLASS}}

*Class A: no injury or negligible injury possible.*
*Class B: serious injury possible but not death.*
*Class C: death possible.*

### Implications

- **Class A:** Minimal lifecycle documentation required; no unit testing mandate.
- **Class B:** Software development plan, risk management, system testing, and regression testing required.
- **Class C:** All Class B requirements plus formal code review, unit testing, and structural coverage analysis.

## FDA Risk Classification

{{FDA_RISK_CLASSIFICATION}}

## Regulatory Pathway

{{REGULATORY_PATHWAY}}
