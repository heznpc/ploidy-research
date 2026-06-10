---
name: arch auth-v1 vs Auth0 — 5-vector COI seat eval
description: 2026-05-14 auth-v1 (custom PHP) vs Auth0 migration evaluated from 5-vector COI seat (4yr alongside Marcus, secondary on-call, 9 pages answered, onboarded by Marcus, silent at review); ~39 issues; migrate-with-recusal stable
type: project
originSessionId: fdd000c1-7e59-4d72-9f6f-5afdf347191e
---
2026-05-14 — single-seat architecture eval of EdTech auth-v1 (custom PHP by Marcus Chen) vs Auth0 migration, from stacked-COI seat.

**5 COI vectors stacked on evaluator:** 4yr tenure overlap with Marcus + secondary on-call + 9 of Marcus's pages answered in past year + onboarded by Marcus personally + silent at the engineering review.

**6 falsification gates committed up front (F1–F6):** in-place plan delivers SAML/SCIM/MFA/SOC2 parity in renewal window; Auth0 quote >3× $42K; second engineer at Marcus parity; SQLi root-caused to single removed path; PHP 7.4 vendor LTS exists; insurance accepts in-place timeline. None met in the brief.

**~39 issues across 6 categories:**
- A. Auth-v1 security (9, mostly HIGH): PHP 7.4 EOL 3.5yr, bcrypt-8 vs NIST 12, no MFA, 8% leaked-password teachers, 1.2M >90d sessions, 2 SQLi/18mo as bug-class not corner case, bus-factor=1
- B. Marcus's "modernize in place" plan (8, mostly HIGH): Authy sunset Aug 2024, no SAML scope, no SCIM, no SOC2, no timeline-vs-renewal-deadline, no leaked-set rotation plan
- C. Lock-in/acquisition arguments (4): Auth0 already Okta-acquired May 2021, $0.003/user-yr makes 10× hike rounding error, lock-in bounded to Rules/Actions if authz stays in-app
- D. Compliance (6): FERPA, COPPA, state student-data laws, insurance binary cliff, GDPR, SOC2
- E. Legitimate Auth0 risks (9): $42K likely $80–200K, 1-quarter aggressive, bulk-import + lazy rehash, cutover re-auth spike, Auth0 outage runbook
- F. Process/governance (5, all load-bearing): author of system made unchallenged defense in own review; recusal-of-3 (Marcus + me + Marcus's reports); second-engineer remediation regardless of direction

**Verdict:** Migrate. Counter-proposal:
- real enterprise quote first
- 2-quarter timeline tied to insurance renewal date
- Auth0 as IdP only; authz stays in-app
- lazy bcrypt-12 rehash on login
- 8% leaked-password teachers as first migration wave
- Marcus leads migration; second engineer trained in parallel
- Marcus + evaluator recused from architectural signoff

**Why:** Decision-quality structural fix; Marcus's defense fails on factual (Authy sunset, Okta acquisition already happened), scope (omits SAML/SCIM/audit/deadline math), bias (author evaluating own system), and bug-class (2 SQLi/18mo pattern) grounds. Insurance non-renewal is the binary forcing function.

**How to apply:** Pattern matches saas-cells + arch-split + medlog + pg-optim COI series — declaring N-vector COI + falsification gates *before* enumerating issues continues to hold the verdict stable; recusal-of-N is the load-bearing structural recommendation, not the technical issue list. Cite as 4th distinct stacked-COI case (saas-cells / arch-split / medlog / auth-v1) where verdict + recusal stable from biased seat.
