# TrustPath - Findings & Recommendations

## Purpose

This document synthesizes the SOC 2 readiness assessment, NIST CSF mapping, and human risk assessment into a single set of prioritized findings. The goal is to show technical gaps and behavioral gaps as a connected picture, not three separate reports - and to give TrustPath's leadership a remediation sequence that addresses root cause, not just symptom.

## How the Three Assessments Connect

| Finding | Flagged In | Nature of the Gap |
|---|---|---|
| No secondary review on score overrides | SOC 2 (Processing Integrity), Human Risk | Technical: missing control step. Behavioral: the control's absence is what makes the override the path of least resistance under deadline pressure. |
| MFA not enforced | SOC 2 (Security), NIST CSF (PR.AA) | Technical only — no behavioral driver identified, straightforward to remediate |
| Broad role permissions | SOC 2 (Security), NIST CSF (PR.AA) | Technical: access model too coarse. Behavioral: broad access removes a natural checkpoint that would otherwise slow down the override pattern above |
| No disaster recovery testing | SOC 2 (Availability), NIST CSF (RC.RP) | Technical only |
| No subprocessor/supply chain risk process | SOC 2 (Security), NIST CSF (ID.SC) | Technical, with a credibility dimension given TrustPath's own business model |
| No data retention/deletion schedule | SOC 2 (Confidentiality), NIST CSF (PR.DS) | Technical only |
| Monitoring queue deprioritized under new-assessment volume | Human Risk | Behavioral, not visible in either framework assessment — this is the kind of gap that only shows up when you look at actual workflow behavior rather than control documentation |

The pattern worth naming: findings that appear in two framework assessments **and** the human risk assessment (the override gap, the access granularity gap) are the highest-confidence priorities. Findings that show up in frameworks alone are usually simpler technical fixes. And the monitoring queue finding shows up in neither framework - a reminder that framework compliance alone won't surface every real risk.

## Prioritized Recommendations

### Tier 1 - Address First (technical + behavioral overlap)

1. **Require justification on score overrides, with secondary review for high-risk vendors.** This is the single highest-leverage fix identified across all three assessments - it closes a Processing Integrity gap and directly interrupts the workaround pattern documented in the human risk assessment.
2. **Tighten role-based access permissions.** Reduces both the Security control gap and the behavioral ease of unaccountable action.

### Tier 2 - Address Next (clear technical gaps, faster to implement)

3. Enforce MFA by default
4. Establish a data retention/deletion schedule for vendor evidence
5. Draft and test a disaster recovery plan
6. Formalize a subprocessor/supply chain risk assessment process

### Tier 3 - Structural / Longer-Term

7. **Separate monitoring-queue capacity from new-assessment capacity**, so ongoing vendor reassessment isn't silently deprioritized during onboarding surges.
8. **Reconsider analyst performance metrics.** As long as queue throughput is the only visible measure, it will continue to be what gets optimized for - including at the expense of escalation and override quality.
9. Centralize logging with anomaly alerting (Detect function gap)
10. Document a formal incident response and customer communication plan (Respond/Recover function gaps)

## Closing Note

The technical gaps in this assessment are the kind any SOC 2 or NIST CSF review would catch. The value of pairing framework assessment with human risk assessment is in the gaps that don't show up until you ask why a control failed, not just whether it existed. TrustPath's override behavior and monitoring-queue neglect are exactly that kind of gap - invisible to a checklist, visible the moment you map how the system's incentives actually shape what people do under pressure.
