# Case Study: Why "Airtight" Controls Fail Under Pressure - A TrustPath Vendor Risk Assessment

*A condensed summary of the human risk assessment from the [grc-trustpath-usable-security](./README.md) portfolio project.*

## The Setup

TrustPath is a fictional B2B SaaS platform used by security and procurement teams to assess and monitor third-party vendors. Like most tools in this space, it looks solid on paper - role-based access, automated risk scoring, a documented vendor evaluation workflow. A standard SOC 2 and NIST CSF review would flag a handful of technical gaps and call it done.

This assessment asked a different question: how do the people actually using this platform behave when they're under deadline pressure - and where does the system's design make the wrong choice the easy one?

## The Finding

TrustPath lets analysts override an automated vendor risk score with a single click. No justification required. No secondary review.

On paper, that's a Processing Integrity gap - a missing control step. In practice, it's something more specific: it's the exact point where a rushed analyst, juggling a backlog of vendor evaluations against a procurement deadline, will choose the one-click path over the multi-day escalation path. Every time.

This isn't a training problem. Analysts aren't overriding scores because they don't understand risk. They're overriding scores because the platform made the risky option the fast one and the careful option the slow one - and then measured them on speed.

## Why This Matters Beyond TrustPath

This is the pattern behind a lot of "control failures" that get written up as human error: the control existed, technically. It just wasn't the path of least resistance. A decade in occupational health and safety taught me this same lesson long before I ever touched a compliance framework - unsafe behavior is almost always a system design failure, not a human failure. The fix isn't a stricter policy or more training. It's redesigning the decision point so the safe choice and the easy choice are the same choice.

## The Fix

Not a ban on overrides — a redesign of what an override costs:

- Require a justification field, so the decision becomes documented instead of invisible
- Route high-risk overrides through a lightweight secondary review
- Stop measuring analysts purely on throughput, since that's what any override-friendly design will optimize for

None of this slows down the legitimate cases. It just makes the shortcut visible instead of silent.

## The Takeaway

Framework compliance tells you whether a control exists. It doesn't tell you whether anyone will actually use it when it's inconvenient. That second question is a UX question, and most GRC assessments never ask it.

---

*Read the full assessment, including the SOC 2 readiness review, NIST CSF mapping, and detailed failure mode analysis: [grc-trustpath-usable-security](./README.md)*
