# GRC103 Lab 4 — Executive Summary & Recommendations

**To:** CISO, Head of HR, Executive Management
**From:** GRC Audit Team (Chioma Ameh, C11/26/CGRCE/17567)
**Date:** November 7, 2026
**Subject:** Results of GRC103 Lab 4 — Controlled Phishing Simulation (Proof-of-Concept)

### 1. Executive Summary

A controlled, internal, benign phishing simulation was conducted as a
**proof-of-concept exercise** using the GoPhish framework in an isolated lab
environment, with a single self-controlled test mailbox standing in for a
target employee. The simulation successfully demonstrated the complete
phishing-simulation lifecycle — campaign setup, benign email delivery via a
sandboxed SMTP relay, fictional landing page interaction, and results
tracking — while surfacing both a behavioral and a tooling finding.

### 2. Key Findings & Metrics

- **Email Open Rate:** 100% — the single target opened the email.
- **Link Click-Through Rate:** 100% — the target clicked the embedded link.
- **Credential Submission Rate:** 0% (recorded) — however, this reflects a
  tracking/instrumentation limitation discovered during the lab (see the
  companion Risk Assessment Table, Limitation #2), not a confirmed absence
  of risk.

**These figures describe a single test subject and must not be
extrapolated to represent organizational-wide risk.** They demonstrate
that the simulation infrastructure works end-to-end and that a realistically
worded urgency-based phishing email can succeed in prompting engagement,
even from a security-aware test subject.

### 3. Risk Analysis

Even at n=1, the 100% open and click rate illustrates a well-established
principle in social engineering: urgency and loss-aversion language (e.g.,
"your password expires in 24 hours," "failure to act will result in loss
of access") is highly effective at prompting action before critical
evaluation. At organizational scale, this pattern — if unaddressed — could
translate into:

- Initial network access for real attackers via stolen credentials
- Data breaches and associated financial loss
- Regulatory exposure (GDPR, NDPR, or other applicable data-protection frameworks)
- Reputational damage

### 4. Recommended Actions

1. **Scale this test properly.** Before any finding is acted upon
   organizationally, repeat this simulation against a statistically
   meaningful sample (minimum several dozen participants) with informed
   consent and proper confidence-interval reporting, as outlined in the
   Quantitative Risk Calculations Study Guide.
2. **Accelerate MFA rollout** across all VPN and critical-system logins —
   the single most effective control against credential-based compromise.
3. **Shift training format** from static annual compliance modules to
   continuous, scenario-based micro-training.
4. **Audit tooling reliability.** Before using GoPhish (or any phishing
   simulation tool) for a live organizational assessment, validate that its
   "Submitted Data" tracking reliably fires under realistic conditions —
   this lab surfaced a gap between actual user action and recorded telemetry
   that could otherwise understate real risk.
5. **Integrate phishing simulations into onboarding** and run them on a
   recurring (e.g., quarterly) cadence once scaled appropriately.

### 5. Conclusion

This lab moved from technical/application security into the human-risk
domain central to GRC practice. It confirmed that the student can configure,
launch, and interpret a phishing simulation end-to-end, while also
practicing the GRC discipline of **distinguishing a genuine security finding
from a tooling artifact** — a distinction that matters greatly when this
kind of data is used to request budget or justify policy change to
leadership.
