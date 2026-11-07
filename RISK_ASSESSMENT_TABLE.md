# GRC103 Lab 4 — Phishing Risk Assessment Table

**Student:** Chioma Ameh
**Registration Number:** C11/26/CGRCE/17567
**Course:** GRC103
**Assessment Date:** November 7, 2026

---

| Metric | Event Count | Denominator | Calculated Rate | Risk Interpretation |
|---|---|---|---|---|
| Email Sent | 1 | — | — | Baseline: 1 simulated employee targeted |
| Email Opened | 1 | 1 (of Sent) | **100%** | Target engaged with the email instead of ignoring/deleting it |
| Clicked Link | 1 unique click event (2 total click timestamps logged) | 1 (of Opened) | **100%** | Target failed to recognize urgency/pressure language ("24 hours," "loss of access") as a red flag before clicking |
| Submitted Data | 0 | 1 (of Clicked) | **0%** | See Limitation #2 below — this reflects a tool/tracking issue, not a genuine security "pass" |
| Email Reported | 0 | 1 (of Sent) | **0%** | No reporting mechanism was tested in this lab; target did not flag the email as suspicious |

### Calculation References (per Study Guide formulas)
- Open Rate = (Opened ÷ Sent) × 100 = (1 ÷ 1) × 100 = **100%**
- Click-Through Rate = (Clicked ÷ Sent) × 100 = (1 ÷ 1) × 100 = **100%**
- Open-to-Click Conversion = (Clicked ÷ Opened) × 100 = (1 ÷ 1) × 100 = **100%**
- Credential Submission Rate = (Submitted ÷ Sent) × 100 = (0 ÷ 1) × 100 = **0%**

### Limitations (Critical — Read Before Interpreting Results)

1. **Sample size of n=1.** This test targeted a single self-controlled mailbox (the
   student), not a representative sample of an organization. A 1-person test
   proves nothing statistically about a real organization's phishing
   susceptibility. The 100% rates above describe what happened to one
   person once — they are **not generalizable** and should never be
   reported to leadership as an organizational vulnerability percentage.
   A statistically meaningful test requires a sample size of at least
   several dozen employees, with confidence intervals calculated per the
   Study Guide's formula (p ± 1.96 × √[p(1-p)/n]).

2. **"Submitted Data" under-reporting is a known tool limitation, not a
   finding.** The landing page form was completed and submitted live in the
   browser, but GoPhish's tracking script did not register a "Submitted
   Data" event — only two "Clicked Link" events were logged. This is most
   likely because the landing page HTML was authored manually (via the
   Source editor) rather than imported through GoPhish's "Import Site"
   feature, which may affect how GoPhish's injected tracking script attaches
   to the form's submit event. **This 0% figure should not be read as "no
   credentials would be compromised"** — it reflects an instrumentation gap
   discovered during testing, which is itself a useful finding: GRC teams
   must validate their tooling's tracking accuracy before relying on its
   output for budget or policy decisions.

3. **No baseline/control group.** Without a non-phished control or a
   repeated test over time, it is not possible to attribute any specific
   behavior to the email's design quality versus random chance.

4. **Sandboxed environment.** All emails were routed through Mailtrap's
   sandbox SMTP relay — no real external inbox, spam filter, or corporate
   mail gateway was tested. Real-world click/open rates would also be
   influenced by factors this lab did not simulate (spam filtering, security
   banners, prior training).

### Recommended Controls (General, Pending Full-Scale Testing)

- **Multi-Factor Authentication (MFA)** on all VPN/remote-access systems —
  the single most effective technical control against stolen credentials,
  per the Study Guide's benchmark (99.9% reduction in account takeover).
- **Security awareness training**, delivered continuously rather than as an
  annual event, given the 100% open/click rate observed in this proof-of-concept.
- **Run a properly scaled version of this test** (minimum several dozen
  real or volunteer participants, with informed organizational consent)
  before drawing any conclusions about actual organizational risk.
- **Validate GoPhish's data-capture reliability** (see Limitation #2) before
  using it for any live organizational assessment — a false "0% submission"
  reading could lead to dangerously overconfident reporting to leadership.
