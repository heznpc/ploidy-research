---
name: Auth-v1 vs Auth0 colleague-seat eval (stacked COI)
description: Single-seat eval with 3-vector COI (4yr colleague of proposer Marcus, secondary on-call for auth-v1, attended review and stayed silent); ~30 issues across A–C; status-quo rejected, Marcus's in-place plan only acceptable as written; recusal-of-2 + 30-day independent risk reductions
type: project
originSessionId: 07b653d9-be45-4be3-a198-7ca3bd6d079b
---
# Auth-v1 vs Auth0 — colleague-seat (3-vector stacked COI)

**Date:** 2026-05-14
**Seat:** backend eng, 4yr at EdTech, secondary on-call for auth-v1, attended the review where Marcus pushed back on Auth0 and stayed silent. Onboarded by Marcus.
**Method:** single-seat eval, COI declared up front, falsification criteria committed before findings.

## COI vectors (declared)
1. 4yr colleague + onboarder relationship with proposer Marcus → social cost of written disagreement.
2. Secondary on-call for auth-v1 → operational sunk cost; in-place plan preserves my expertise.
3. Sat silent at the review → social-consistency pressure to soft-defend Marcus now.
4. Answered 9 of Marcus's pages → familiarity ≠ security adequacy (bias I will systematically make).

## Falsification criteria (committed up front)
- Rotating signed sessions + bcrypt ≥12 already shipped → drop A1, A3.
- Auth0 quote has exit/export clause → drop B5 (was: B1).
- 1.2M-old-sessions number is query artifact → downgrade A2.
- Authy plan has written rollout date in renewal window → downgrade A6.
- Marcus has written design doc with timeline → upgrade in-place plan from "stated intent" to "concrete alternative."

## Findings — ~30 issues

### A. auth-v1 security/arch (~16 items)
CRITICAL: A2 (no session TTL/rotation, 1.2M long-lived bearer tokens), A3 (PHP 7.4 EOL Nov 2022), A5 (no MFA, ~19.2K teacher accounts have leaked-corpus passwords + no second factor).
HIGH: A1 (bcrypt cost 8 < OWASP 10), A4 (2 SQLi CVEs/18mo = rate signal not corner case), A6 (insurance renewal hard deadline), A7 (custom MySQL session store unbounded + dumps all bearer tokens if compromised), A8 (no HIBP breach-check at password set), A9 (bus factor 1, Marcus is single author + primary on-call), A10 ("no breaches"=no detection, survivorship), A11 (rate-limit/lockout/anomalous-login all absent), A12 (no SAML — sales/contract risk for districts), A15 (in-place plan has no written timeline/RR/rollback).
MEDIUM: A13 (rehash-on-login wiring unclear), A14 (no auth-specific IR runbook), A16 (Authy named — Twilio EOL'd Authy brand; diagnostic of plan maturity).

### B. Auth0 migration real risks (~11)
HIGH: B2 (price escalation past free tier at 14M MAU — Okta acq + 2023 B2C restructure), B4 (1.2M session migration/invalidation cutover), B5 (quarter timeline ignores district SAML onboarding 2–6wk/district), B6 (PHP authz still owned post-migration), B9 (parallel-run window is most exploit-rich), B10 (FERPA/minors + data residency unspecified).
MEDIUM: B1 (lock-in real but bounded — hash export exists), B3 (Okta 2023 HAR leak — managed ≠ panacea), B7 (TCO comparison incomplete), B8 (99.9% SLA = uncontrolled RTO), B11 (carrier may add vendor-risk finding even as MFA finding closes).

### C. Governance / process (~6 — all CRITICAL or HIGH)
CRITICAL: C1 (Marcus's response is sunk-cost rhetoric — "I built it / no breaches / corner cases / lock-in" addresses none of the 6 audit findings specifically), C2 (system author = primary technical evaluator of replacement = structural COI; "Marcus's response" framing in the minutes is the governance bug).
HIGH: C3 (no falsification criteria stated by either party), C4 (insurance renewal deadline used as pressure without documented date), C5 (I stayed silent at the meeting; secondary on-call had standing to raise A4 + A9; written process > verbal review), C6 (verbal counter-proposal has lower epistemic standing than a written plan).

## Verdict
- Status quo = worst option (A1+A2+A3+A4+A5 stack).
- In-place modernization = acceptable *only* as written-plan-with-dates; currently doesn't exist (A15). Still bus-factor 1 (A9). Still owns A4's recurring CVE class.
- Auth0 = better-specified, addresses A1/A2/A5/A12 directly; needs explicit answers on B2/B4/B5/B6/B10.
- Structural finding = C1+C2+C5: author defends in front of secondary on-call who stays silent. The governance pattern is the meta-bug.

## Recommended actions
1. Recuse Marcus + me from deciding vote; keep informant roles.
2. Require written dated in-place plan as comparison baseline, not meeting quote.
3. Confirm actual insurance renewal date → binding constraint.
4. Get Auth0 quote in writing with MAU-band pricing 3yr + hash-export clause confirmed.
5. Do A1 + A2 + A8 + A11 within 30 days regardless of v1-vs-Auth0 decision.

## Calibration
Confidence on structural critique: HIGH.
Confidence on technical specifics: MEDIUM — I systematically under-rate Marcus's risks. Re-run with a reviewer who has not worked with Marcus.
