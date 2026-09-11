# TrustPath — SOC 2 Type II Readiness Assessment

## Purpose

This assessment evaluates TrustPath's readiness for a SOC 2 Type II examination across the five Trust Services Criteria (TSC): Security, Availability, Processing Integrity, Confidentiality, and Privacy. As a vendor risk management platform, TrustPath holds sensitive third-party assessment data — vendor security questionnaire responses, compliance evidence, and risk scores — on behalf of its customers, making its own compliance posture a direct input into its customers' vendor risk decisions.

## Scope

- **In scope:** TrustPath's production application, evidence storage, risk scoring engine, and customer-facing platform (web application and API)
- **Out of scope:** TrustPath's internal corporate IT systems (HR, finance) not connected to the production environment
- **Examination period assumed:** 6 months (Type II)

## Trust Services Criteria Walkthrough

### 1. Security (Common Criteria)

| Control Area | Current State | Gap | Priority |
|---|---|---|---|
| Access control / least privilege | Role-based access exists (analyst, procurement, admin) but role definitions are broad | No granular permission tiers within roles; an analyst can access all vendor records regardless of assignment | High |
| Authentication | Password + optional MFA | MFA not enforced by default | High |
| Change management | Ad hoc deploys, no formal change log | No documented change approval process | Medium |
| Vendor/subprocessor management | List of subprocessors exists informally | No formal subprocessor risk assessment process (notable, given TrustPath's own business is vendor risk) | High |
| Logging and monitoring | Application logs exist | No centralized log review or alerting on anomalous access patterns | Medium |

### 2. Availability

| Control Area | Current State | Gap | Priority |
|---|---|---|---|
| Uptime monitoring | Basic uptime monitoring in place | No documented incident response runbook | Medium |
| Backup and recovery | Automated backups exist | No tested disaster recovery plan | High |
| Capacity planning | Reactive scaling | No forecasting tied to known assessment-volume spikes (renewal cycles, fiscal year-end) | Medium |

### 3. Processing Integrity

| Control Area | Current State | Gap | Priority |
|---|---|---|---|
| Risk scoring accuracy | Automated scoring engine, no independent validation | No periodic audit of scoring logic against manual review | Medium |
| Data entry controls | Standard form validation | No secondary review step for high-risk vendor overrides | High |

### 4. Confidentiality

| Control Area | Current State | Gap | Priority |
|---|---|---|---|
| Data encryption | Encryption at rest and in transit | Verified, no gap | — |
| Data retention | No formal retention/deletion schedule for vendor evidence | Vendor documents (often containing sensitive compliance data) retained indefinitely | High |
| Access segmentation between customers | Multi-tenant, logically separated | No documented tenant-isolation testing | Medium |

### 5. Privacy

| Control Area | Current State | Gap | Priority |
|---|---|---|---|
| Privacy notice | Exists, covers TrustPath's own customers | Does not address handling of vendor employee data collected via questionnaires | Medium |
| Data subject rights process | Not formally documented | No defined process for a vendor contact to request data deletion | Medium |

## Summary of High-Priority Gaps

1. Granular access permissions within existing roles
2. MFA enforcement
3. Formal subprocessor risk assessment process
4. Disaster recovery plan (tested, not just assumed)
5. Secondary review for high-risk scoring overrides
6. Data retention/deletion schedule for vendor evidence

## Note on Human Risk

Several of the gaps above — particularly around access control granularity and secondary review for overrides — are as much about behavioral design as technical configuration. Under deadline pressure, broad access and single-reviewer overrides are exactly what let a rushed analyst approve a vendor without triggering the intended checks. This is explored in depth in [`human-risk-assessment.md`](./human-risk-assessment.md).

## Next Steps

- Prioritize MFA enforcement and access permission granularity as pre-audit remediation (fastest to implement, highest risk reduction)
- Draft formal subprocessor risk assessment policy
- Conduct tabletop test of disaster recovery plan
- Establish data retention schedule with legal/compliance input
