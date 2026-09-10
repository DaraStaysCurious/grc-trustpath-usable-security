# TrustPath Usable Security Assessment

## Overview

TrustPath is a fictional B2B SaaS vendor risk management platform — the kind of tool security and procurement teams use to assess, score, and monitor their third-party vendors. This project is a compliance and human-risk assessment of TrustPath's SOC 2 and NIST CSF posture, conducted from the perspective of a GRC analyst brought in to evaluate both the technical control environment and the human behavior that environment produces.

## Why This Project Is Different

The other assessments in this portfolio apply a human-factors lens as a layer on top of a standard framework review. This one doesn't. TrustPath gives human risk its own dedicated assessment — [`human-risk-assessment.md`](./human-risk-assessment.md) — built using UX research methods (user journey mapping, failure mode analysis, behavioral observation) applied directly to security control design, not bolted on afterward.

## The Core Tension

TrustPath's users — security and procurement teams — operate under significant time pressure, often evaluating dozens of vendors simultaneously against hard deadlines. That pressure creates predictable workaround behavior. Controls that look airtight on paper are frequently the ones most likely to get bypassed when a procurement deadline is looming. This assessment treats that pressure as a design input, not a footnote.

## Scope

- **Frameworks assessed:** SOC 2 Type II (Trust Services Criteria), NIST CSF
- **Industry:** B2B SaaS, vendor/third-party risk management
- **Assessment type:** Readiness assessment + human-risk assessment

## Contents

| Document | Description |
|---|---|
| [`company-profile.md`](./company-profile.md) | TrustPath's fictional company background, user base, and operating environment |
| [`soc2-readiness-assessment.md`](./soc2-readiness-assessment.md) | SOC 2 Type II gap analysis across the Trust Services Criteria |
| [`nist-csf-mapping.md`](./nist-csf-mapping.md) | Function-by-function NIST CSF mapping |
| [`human-risk-assessment.md`](./human-risk-assessment.md) | User journey mapping, failure mode analysis, and behavioral observation of workaround-driving pressure points |
| [`findings-and-recommendations.md`](./findings-and-recommendations.md) | Synthesized findings connecting technical gaps to human-risk findings, with prioritized remediation |

## Methodology Note

This assessment draws on a decade of occupational health and safety risk methodology alongside UX research practice — the same cross-disciplinary approach used across this portfolio. The underlying thesis: unsafe (or non-compliant) behavior is a system design failure, not a human failure.
