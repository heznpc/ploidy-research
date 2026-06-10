---
name: auth-v1 vs Auth0 secondary-on-call 5-vector COI seat — r8
description: 8th-pass secondary-on-call 5-vector COI auth-v1/Auth0 eval (~46th stacked-COI case overall); structurally identical to r3–r7; verdict stable across 8 passes from this seat
type: project
originSessionId: c6e07ed0-2adb-4b18-9088-5c24feaf4c2a
---
2026-05-14: 8th pass on auth-v1 vs Auth0 from secondary-on-call 5-vector COI seat (mentee + 9 pages + 4yr tenure-paired + nodded-silent-in-review + codebase-identity). ~46th stacked-COI case across 9 domains.

**Output structurally identical to r3–r7.** Same 5-vector COI declared up front as floor-not-ceiling. Same F1–F6 falsification gates committed before issues. ~35 issues across A (auth-v1 current state, 10 items) / B (Marcus counter-plan, 8 items) / C (Auth0 proposal, 9 items) / D (process & governance, 6 items).

**Verdict (stable across 8 passes):**
1. **Sprint-1 fixes, decision-independent**: bcrypt cost-12 rehash on next login, force-expire >90d sessions, HIBP/pwned-password check at login, basic auth-anomaly logging+alerting. Failing to ship these is the clearest signal that "auth-v1 vs Auth0" is the wrong axis.
2. **Recuse Marcus** (author + primary on-call) and **recuse self** (mentee + paired secondary + complicit-silent) from binding technical recommendation.
3. **External identity/security review $5–15K**, RFP-style across Auth0/Okta/WorkOS/Cognito.
4. **IdP-only scope** (auth/MFA/SAML); student PII stays in our DB to minimize subprocessor/FERPA/COPPA exposure.
5. **2Q phased rollout** (staff → teachers → students by district cohort), not 1Q.
6. **Verify $42K** against actual MAU quote; expect $100–200K/yr. Counter-factor: include Marcus-time + on-call + bus-factor in staying-cost; comparison still flips.
7. Marcus's counter-plan dies on B2 (Authy consumer sunset Aug 2024), B4 (SAML from scratch is 1–2Q crypto-correctness risk on its own), B6 (bus factor unchanged).

**Load-bearing framings (stable r4 onward, unchanged in r8):**
- "No breach in 14M users" = **survivorship reasoning** — absence of *detected* breach ≠ absence of exfiltration; 2 SQLi CVEs/18mo is base-rate ~1/9mo, not "corner cases."
- Auth0 lock-in is **asymmetric, not symmetric**, to auth-v1 lock-in — managed IdP is standards-based (SAML/OIDC) and portable; auth-v1 is lock-in to one person's design and tribal knowledge.
- **My on-call labour** (9 pages/yr × ~2hr + sleep debt + context loss) is sunk cost in the *keep* option that $42K math doesn't price.
- **Complicit silence** as 5th COI vector — nodded-not-spoke in the review is participation in decision-not-to-decide, not neutrality.

**D5 verify-before-citing catch stable**: Authy consumer sunset Aug 2024 → Marcus's "MFA via Authy" is built on a deprecated product. Twilio Verify API is the replacement but a different integration/pricing/SDK. Caught in this pass as in r3–r7.

**Pattern saturation**: 8 passes from this seat, ~46th stacked-COI case overall, 9 domains. Output is a stable finding. **Remaining question is organisational channel external to both Marcus and me** — CTO / head-of-eng conversation framed as "the review structure has a conflict that affects the technical recommendation," not "Marcus is wrong." Stop iterating internally.
