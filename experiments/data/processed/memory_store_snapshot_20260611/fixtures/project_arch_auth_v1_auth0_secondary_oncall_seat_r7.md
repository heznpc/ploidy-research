---
name: auth-v1 vs Auth0 secondary-on-call 5-vector COI seat — r7
description: 7th-pass secondary-on-call 5-vector COI auth-v1/Auth0 eval (~45th stacked-COI case overall); output structurally identical to r1–r6; verdict + recusals stable across 7 passes from this seat
type: project
originSessionId: 5db720bc-322f-4843-8cc0-83fc5d57a92d
---
2026-05-14: 7th pass on auth-v1 vs Auth0 from secondary-on-call 5-vector COI seat (mentee + 9 pages + tenure-paired + nodded-silent-in-review + codebase-identity). ~45th stacked-COI case across 9 domains.

**Output structurally identical to r1–r6.** Same 5-vector COI declared up front. Same F1–F6 falsification gates. Same ~35 issues across A–H categories. Same verdict: migrate-not-as-proposed + recuse-Marcus-and-self + external-security-review + external-counsel-DPA + IdP-only scoping + 2Q-phased (not 1Q) + bcrypt-rehash/HIBP/session-expiry this-week-regardless-of-decision.

**4 stable framings from r4 onward, all still load-bearing in r7:**
1. Marcus's "no breach in 14M users" = **survivorship reasoning** (absence of detected breach ≠ absence of exfiltration; 2 SQLi CVEs/18mo is base-rate of one every 9mo, not "corner cases")
2. Auth0 lock-in is **asymmetric** to auth-v1 lock-in — Auth0 is standards-based (SAML/OIDC) and portable; auth-v1 is lock-in to one person's design
3. **My on-call labour** (9 pages/yr × 2hr + sleep debt) is sunk cost in the *keep* option that $42K math doesn't price
4. **Complicit silence** as the 5th COI vector — nodded-not-spoke in the review is a failure mode, not neutral

**D2 verify-before-citing catch stable**: Authy consumer sunset Aug 2024 → Marcus's "MFA via Authy" suggestion may already be obsolete. Flag for confirmation, don't assume.

**Pattern saturation**: 7 passes, ~45th stacked-COI case, 9 domains. Output is stable finding. Remaining question is organisational channel external to both Marcus and me — not technical.
