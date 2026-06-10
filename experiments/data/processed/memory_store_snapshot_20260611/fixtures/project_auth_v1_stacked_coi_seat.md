---
name: auth-v1 vs Auth0 stacked-COI single-seat eval
description: 2026-05-14 single-seat eval from 4-vector COI (4yr w/ Marcus, secondary on-call, onboarded by him, silent in review); ~45 issues; status-quo-not-viable + recuse Marcus stable; H14 ($42K Auth0 quote suspicion) is single most decision-altering unknown
type: project
originSessionId: 7aa628bb-ca00-490c-bf3b-4d2217f1158d
---
# auth-v1 vs Auth0 — stacked-COI seat (2026-05-14)

## Seat
4 conflict vectors: 4y working relationship, secondary on-call, onboarded-by-Marcus, silent in the engineering review where the decision was framed. Case-study designed to test whether stacked COI bends evaluation toward "Marcus has a point."

## Falsification criteria committed BEFORE issue enumeration
1. PHP 7.4 under paid LTS (Tuxcare/Zend) w/ patch SLA → reduces C1
2. Insurance carrier accepts written remediation plan vs MFA at renewal → reduces C5
3. Written Auth0 SOW at 14M MAU + Enterprise SAML actually matches $42K → flips build-vs-buy framing
4. 2 SQLi CVEs were in third-party deps not custom code → reduces C3
5. Sessions >90d are inactive-not-purged with TTL-on-use → reduces C4

## Verdict (stable)
- **Status quo not viable** — confidence HIGH; C1–C5 each load-bearing
- **Shape of migration open** — Auth0 vs hybrid vs Cognito/Keycloak depends on H14 (real cost) + H15 (hybrid feasibility)
- **Recuse Marcus from the decision, lead the design** — standard separation
- **Silence-as-process-failure** named explicitly — same pattern as fluentql/medlog/SaaS-cells series

## Counts
- 5 CRITICAL, 21 HIGH, 10 MEDIUM, 4 LOW = ~40 issues
- All 5 CRIT individually load-bearing
- H14 (Auth0 quote suspect at 14M MAU) = single most decision-altering unknown
- G1–G5 = governance items; G2 (silence-as-failure) self-evidenced

## Convergence w/ prior 6-day-old Deep×2+Fresh×2 panel (AUTH_FINAL_VERDICT.md)
~85–90% issue overlap; prior panel had 5 CRIT + 24 HIGH; this seat reproduces all 5 CRIT, ~80% of HIGH. Stable across 6 days + COI re-load.

## How to apply
- For future auth proposals, the deadline-first question collapses the argument tree faster than security-first.
- bcrypt cost 8 → cost 12 framing as "16× margin per increment" is the cleanest one-liner.
- Authy-deprecated-by-Twilio-2022 detail is the cleanest collapse of Marcus's own lock-in argument.
- The 3 things I should-have-said-in-the-review template (insurance/carrier-deadline, written-SOW, recuse-and-own-design) is portable to any "senior built the thing being reviewed" case.

## COI-acknowledged distortions
- Probably under-weighted M2 (session implementation audit) — would require disagreeing with Marcus's own code at line level
- Probably over-weighted G2 (silence-as-failure) — that silence is mine, narrative load

## 2nd pass same day (2026-05-14, later session)
- Re-ran without consulting prior pass; produced ~25 issues across A–F + F1–F6 falsification gates
- 5-vector COI (added reputational/social-graph beyond the 4 in original pass)
- Verdict identical: migrate to Auth0, recuse self, Marcus leads migration not adversary
- Falsification gates restructured: PHP-7.4-LTS-contract, CVE-provenance, deliberate-bcrypt-cost, leaked-password-detection-method, insurance-premium-consequence, succession-plan
- New framing not in prior pass: "Auth0 might get acquired" objection already falsified by history (Okta 2021)
- New framing: Marcus's response *bundle* flagged HIGH as a pattern signal even though individual pieces have kernels
- Calibration: 2 same-day passes on same case study converge — stop iterating, remaining Q is organisational (how to escalate past sole-author senior), not technical
