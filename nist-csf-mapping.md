# TrustPath - NIST CSF 2.0 Mapping

## Purpose

This document maps TrustPath's current security posture against the NIST Cybersecurity Framework (CSF) 2.0 functions: Govern, Identify, Protect, Detect, Respond, and Recover. Where the SOC 2 assessment evaluates readiness for a formal audit, this mapping takes a broader risk-management view - useful both for internal prioritization and for demonstrating framework fluency to customers who use NIST CSF as their own reference model.

## Scope

Same system scope as the SOC 2 assessment: TrustPath's production application, evidence storage, risk scoring engine, and customer-facing platform.

## Function-by-Function Mapping

### GOVERN (GV)

| Subcategory | Current State | Gap |
|---|---|---|
| GV.OC - Organizational Context | Informal understanding of TrustPath's role in customers' compliance chains | Not formally documented anywhere customer-facing |
| GV.RM - Risk Management Strategy | Risk decisions made ad hoc by engineering/leadership | No documented risk management strategy or risk appetite statement |
| GV.RR - Roles, Responsibilities, Authorities | Roles exist informally (security lead, engineering lead) | No RACI or formal accountability matrix for security decisions |
| GV.PO - Policy | Some internal policies exist | Not centralized, versioned, or regularly reviewed |

### IDENTIFY (ID)

| Subcategory | Current State | Gap |
|---|---|---|
| ID.AM - Asset Management | Cloud infrastructure inventory exists informally | No formal, maintained asset inventory |
| ID.RA - Risk Assessment | This document and the SOC 2 assessment are the first formal risk assessments | No recurring risk assessment cadence established |
| ID.SC - Supply Chain Risk Management | Subprocessor list exists | No formal supply chain risk assessment process (echoes the SOC 2 gap - notable given TrustPath's own product is supply chain/vendor risk management) |

### PROTECT (PR)

| Subcategory | Current State | Gap |
|---|---|---|
| PR.AA - Identity Management, Authentication, Access Control | Role-based access; MFA optional | MFA not enforced; role permissions too broad (same gap flagged in SOC 2) |
| PR.DS - Data Security | Encryption at rest/in transit | No data retention/deletion schedule (same gap flagged in SOC 2) |
| PR.PS - Platform Security | Standard deployment practices | No formal change management or configuration baseline |
| PR.AT - Awareness and Training | No formal security awareness program for TrustPath's own staff | Notable gap for a company whose product depends on customers' security awareness maturity |

### DETECT (DE)

| Subcategory | Current State | Gap |
|---|---|---|
| DE.CM - Continuous Monitoring | Application logs collected | No centralized log review, no anomaly alerting |
| DE.AE - Adverse Event Analysis | No formal event analysis process | Detection is reactive, dependent on manual discovery |

### RESPOND (RS)

| Subcategory | Current State | Gap |
|---|---|---|
| RS.MA - Incident Management | No documented incident response plan | High-priority gap — same finding as SOC 2 Availability section |
| RS.CO - Incident Communication | No defined customer notification process for a security incident | Would directly affect customers relying on TrustPath for their own vendor risk reporting |

### RECOVER (RC)

| Subcategory | Current State | Gap |
|---|---|---|
| RC.RP - Recovery Planning | Automated backups exist | No tested disaster recovery plan (same finding as SOC 2 Availability section) |
| RC.CO - Recovery Communication | Not defined | No plan for how recovery status would be communicated to customers |

## Cross-Framework Observations

Several gaps surface independently in both the SOC 2 assessment and this NIST CSF mapping — MFA enforcement, access permission granularity, disaster recovery testing, and subprocessor/supply chain risk assessment chief among them. When a gap shows up under two different framework lenses, that's a strong signal it's a genuine structural weakness rather than an artifact of one framework's specific requirements - these should be treated as the highest-confidence remediation priorities.

The supply chain risk management gap (ID.SC) is particularly notable given TrustPath's business model: a vendor risk management platform that hasn't formalized its own vendor/subprocessor risk process is a credibility risk as much as a compliance one.

## Next Steps

- Prioritize the cross-framework gaps identified above (MFA, access granularity, DR testing, subprocessor risk process) as they carry weight in both assessments
- Use this mapping alongside the SOC 2 assessment when presenting findings to leadership, since the dual-framework confirmation strengthens the case for remediation investment
