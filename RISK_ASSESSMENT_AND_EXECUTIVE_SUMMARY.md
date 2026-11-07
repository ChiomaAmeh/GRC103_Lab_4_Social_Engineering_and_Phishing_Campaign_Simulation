# GRC103 Lab 4 - Phishing Risk Assessment Table & Executive Summary

**Student:** Chioma Ameh

**Registration Number:** C11/26/CGRCE/17567

**Course:** GRC103 Social Engineering and Phishing Campaign Simulation

**Assessment Date:** November 7, 2026

---

## Part A - Phishing Risk Assessment Table

| Metric | Event Count | Denominator | Calculated Rate | Risk Interpretation |
|---|---|---|---|---|
| Email Sent | 1 | - | - | Baseline: 1 simulated employee targeted |
| Email Opened | 1 | 1 (of Sent) | **100%** | Target engaged with the email instead of ignoring/deleting it |
| Clicked Link | 1 unique click event (2 total click timestamps logged) | 1 (of Opened) | **100%** | Target failed to recognize urgency/pressure language ("24 hours," "loss of access") as a red flag before clicking |
| Submitted Data | 0 | 1 (of Clicked) | **0%** | See Limitation #2 below - this reflects a tool/tracking issue, not a genuine security "pass" |
| Email Reported | 0 | 1 (of Sent) | **0%** | No reporting mechanism was tested in this lab; target did not flag the email as suspicious |

### Calculation References (per Study Guide formulas)
- Open Rate = (Opened ÷ Sent) × 100 = (1 ÷ 1) × 100 = **100%**
- Click-Through Rate = (Clicked ÷ Sent) × 100 = (1 ÷ 1) × 100 = **100%**
- Open-to-Click Conversion = (Clicked ÷ Opened) × 100 = (1 ÷ 1) × 100 = **100%**
- Credential Submission Rate = (Submitted ÷ Sent) × 100 = (0 ÷ 1) × 100 = **0%**

### Limitations (Critical - Read Before Interpreting Results)

1. **Sample size of n=1.** This test targeted a single self-controlled mailbox (the
   student), not a representative sample of an organization. A 1-person test
   proves nothing statistically about a real organization's phishing
   susceptibility. The 100% rates above describe what happened to one
   person once - they are **not generalizable** and should never be
   reported to leadership as an organizational vulnerability percentage.
   A statistically meaningful test requires a sample size of at least
   several dozen employees, with confidence intervals calculated per the
   Study Guide's formula (p ± 1.96 × √[p(1-p)/n]).

2. **"Submitted Data" under-reporting is a known tool limitation, not a
   finding.** The landing page form was completed and submitted live in the
   browser, but GoPhish's tracking script did not register a "Submitted
   Data" event - only two "Clicked Link" events were logged. This is most
   likely because the landing page HTML was authored manually (via the
   Source editor) rather than imported through GoPhish's "Import Site"
   feature, which may affect how GoPhish's injected tracking script attaches
   to the form's submit event. **This 0% figure should not be read as "no
   credentials would be compromised"** - it reflects an instrumentation gap
   discovered during testing, which is itself a useful finding: GRC teams
   must validate their tooling's tracking accuracy before relying on its
   output for budget or policy decisions.

3. **No baseline/control group.** Without a non-phished control or a
   repeated test over time, it is not possible to attribute any specific
   behavior to the email's design quality versus random chance.

4. **Sandboxed environment.** All emails were routed through Mailtrap's
   sandbox SMTP relay - no real external inbox, spam filter, or corporate
   mail gateway was tested. Real-world click/open rates would also be
   influenced by factors this lab did not simulate (spam filtering, security
   banners, prior training).

### Recommended Controls (General, Pending Full-Scale Testing)

- **Multi-Factor Authentication (MFA)** on all VPN/remote-access systems -
  the single most effective technical control against stolen credentials,
  per the Study Guide's benchmark (99.9% reduction in account takeover).
- **Security awareness training**, delivered continuously rather than as an
  annual event, given the 100% open/click rate observed in this proof-of-concept.
- **Run a properly scaled version of this test** (minimum several dozen
  real or volunteer participants, with informed organizational consent)
  before drawing any conclusions about actual organizational risk.
- **Validate GoPhish's data-capture reliability** (see Limitation #2) before
  using it for any live organizational assessment - a false "0% submission"
  reading could lead to dangerously overconfident reporting to leadership.

---

## Part B - Executive Summary & Recommendations

**To:** CISO, Head of HR, Executive Management

**From:** GRC Audit Team (Chioma Ameh)

**Date:** November 7, 2026

**Subject:** Results of GRC103 Lab 4 - Controlled Phishing Simulation (Proof-of-Concept)

### 1. Executive Summary

A controlled, internal, benign phishing simulation was conducted as a
**proof-of-concept exercise** using the GoPhish framework in an isolated lab
environment, with a single self-controlled test mailbox standing in for a
target employee. The simulation successfully demonstrated the complete
phishing-simulation lifecycle - campaign setup, benign email delivery via a
sandboxed SMTP relay, fictional landing page interaction, and results
tracking - while surfacing both a behavioral and a tooling finding.

### 2. Key Findings & Metrics

- **Email Open Rate:** 100% - the single target opened the email.
- **Link Click-Through Rate:** 100% - the target clicked the embedded link.
- **Credential Submission Rate:** 0% (recorded) - however, this reflects a
  tracking/instrumentation limitation discovered during the lab (see Risk
  Table, Limitation #2), not a confirmed absence of risk.

**These figures describe a single test subject and must not be
extrapolated to represent organisational-wide risk.** They demonstrate
that the simulation infrastructure works end-to-end and that a realistically
worded urgency-based phishing email can succeed in prompting engagement,
even from a security-aware test subject.

### 3. Risk Analysis

Even at n=1, the 100% open and click rate illustrates a well-established
principle in social engineering: urgency and loss-aversion language (e.g.,
"your password expires in 24 hours," "failure to act will result in loss
of access") is highly effective at prompting action before critical
evaluation. At organizational scale, this pattern - if unaddressed - could
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
2. **Accelerate MFA rollout** across all VPN and critical-system logins -
   the single most effective control against credential-based compromise.
3. **Shift training format** from static annual compliance modules to
   continuous, scenario-based micro-training.
4. **Audit tooling reliability.** Before using GoPhish (or any phishing
   simulation tool) for a live organizational assessment, validate that its
   "Submitted Data" tracking reliably fires under realistic conditions -
   this lab surfaced a gap between actual user action and recorded telemetry
   that could otherwise understate real risk.
5. **Integrate phishing simulations into onboarding** and run them on a
   recurring (e.g., quarterly) cadence once scaled appropriately.

### 5. Conclusion

This lab moved from technical/application security into the human risk
domain central to GRC practice. It confirmed that the student can configure,
launch, and interpret a phishing simulation end-to-end, while also
practicing the GRC discipline of **distinguishing a genuine security finding
from a tooling artifact** - a distinction that matters greatly when this
kind of data is used to request budget or justify policy change to
leadership.
