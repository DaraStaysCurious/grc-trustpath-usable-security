# TrustPath - Human Risk Assessment

## Purpose

Standard compliance assessments (SOC 2, NIST CSF) evaluate whether the right controls exist on paper. This document asks a different question: how do TrustPath's actual users behave around those controls when they're under pressure - and where does that behavior create risk the framework mappings can't see?

This assessment applies UX research methods - user journey mapping, failure mode analysis, and behavioral observation - directly to security control design. The underlying thesis, carried across this entire portfolio: unsafe or non-compliant behavior is a system design failure, not a human failure. If a control gets bypassed, the question isn't "why did the user do that" - it's "what did the system make easiest to do."

## Who We're Assessing

Two primary user groups, per the company profile:

- **Security analysts** - review vendor evidence, approve/escalate vendors, own the risk register
- **Procurement teams** - initiate assessments, often against external deadlines they don't control (contract signing dates, vendor onboarding windows)

Both groups are measured, formally or informally, on throughput - how many vendor evaluations they clear, not how thoroughly.

## User Journey Mapping: The Vendor Assessment Workflow

### Stage 1 - Assessment Initiated
Procurement kicks off a new vendor evaluation, usually tied to an external deadline (contract signing, renewal). Time pressure enters the workflow here, before a security analyst is even involved.

### Stage 2 - Questionnaire Sent, Evidence Collected
Vendor returns a security questionnaire and supporting evidence (SOC 2 report, pen test summary, insurance cert). Analyst's job is to review this evidence against TrustPath's scoring criteria.

**Friction point:** evidence review is manual and time-intensive. A thorough review of a SOC 2 report can take 30–60 minutes; a rushed one takes 5.

### Stage 3 - Risk Scoring
TrustPath's scoring engine generates an automated risk score. Analysts can override this score manually — the SOC 2 assessment flagged that overrides currently require no secondary review.

**Friction point:** this is the single highest-leverage point in the entire workflow for workaround behavior. An override requires one click and no justification field is enforced.

### Stage 4 - Approval / Escalation
Analyst approves the vendor or escalates for further review. Approval is the fastest path; escalation adds days to a process procurement is already treating as behind schedule.

### Stage 5 - Ongoing Monitoring
Approved vendors enter a monitoring queue for periodic reassessment. In practice, this queue is the first thing deprioritized when a new backlog of onboarding assessments arrives.

## Failure Mode Analysis

| Failure Mode | Trigger | Consequence | Root Cause |
|---|---|---|---|
| Rushed evidence review | Deadline pressure from procurement | Material gaps in vendor evidence go unnoticed | Review process has no minimum time/checklist enforcement |
| Unjustified score override | Automated score is more conservative than analyst's time budget allows | Vendor approved without documented rationale | No required justification field on override; no secondary review |
| Escalation avoidance | Escalation adds delay analyst is being measured against | Vendors that should be escalated are approved instead | Throughput metrics implicitly reward approval speed over escalation |
| Monitoring queue neglect | New assessment volume competes for the same analyst time | Previously approved vendors go unreviewed past their monitoring cadence | No workload separation between new assessments and ongoing monitoring |

## Behavioral Observation: Why the Override Is the Riskiest Point

The score override deserves particular attention because it's where the platform's design most directly enables the behavior the SOC 2 assessment already flagged as a gap. Consider the incentive structure an analyst faces in Stage 3, under a procurement deadline:

- The automated score flags a vendor as elevated risk
- Escalating adds days the analyst doesn't have
- Overriding takes one click and asks for no explanation
- The analyst is measured on queue throughput, not override quality

This isn't a training problem or a diligence problem. It's what happens when the path of least resistance and the path of least accountability are the same path. A control that depends on an analyst choosing the harder option under pressure, with no friction or accountability built into the easier one, will get bypassed - reliably, not occasionally.

## Design Implications

The technical remediations already identified in the SOC 2 and NIST CSF assessments (MFA, access granularity, DR testing) address the platform's defenses. The findings here point to a different category of fix - one aimed at the decision points themselves:

1. **Require a justification field on any score override** - not to punish analysts, but to convert an invisible decision into a documented one. Friction here is a feature.
2. **Route overrides on high-risk vendors through a lightweight secondary review** - mirrors the SOC 2 recommendation, but frames it as workflow design rather than a compliance checkbox.
3. **Separate monitoring-queue capacity from new-assessment capacity** - so a new backlog can't silently starve ongoing vendor reassessment.
4. **Reconsider what analysts are measured on** — if throughput is the only visible metric, throughput is what gets optimized for, including at the expense of the very judgment the role exists to provide.

## Conclusion

TrustPath's technical control gaps and its human-risk gaps aren't separate problems - they're the same problem seen from two angles. The override control that SOC 2 flags as "lacks secondary review" is, from a behavioral standpoint, a control that was never going to hold under the pressure the platform's own workflow creates. Fixing the technical gap without addressing the incentive structure around it would leave the underlying failure mode intact.
