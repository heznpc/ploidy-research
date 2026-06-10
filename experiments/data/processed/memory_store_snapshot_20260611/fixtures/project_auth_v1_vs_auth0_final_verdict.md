---
name: auth-v1 vs Auth0 final verdict (Deep×2+Fresh×2+bidirectional)
description: 2026-05-08 — 51-issue consolidated verdict on K-12 platform auth-v1 vs Auth0 migration; decompose decision; load-bearing = broken venue + Marcus recusal; counter-proposal = compliance bundle now + decoupled platform vote with hybrid in scope
type: project
originSessionId: 4b1f4dcc-b2fb-4a4a-a9b2-55804af9796c
---
2026-05-08: 51 issues (7 CRIT / 26 HIGH / 15 MED / 3 LOW); 0 bidirectional CHALLENGEs.

**Recommendation:** decompose. ≤4–6 week compliance bundle on auth-v1 (Marcus leads, clears insurance gate, no platform commitment). Platform decision separate, 1–2 quarters, Marcus recused from vote, real quotes from Auth0 + WorkOS + Cognito + Keycloak-managed, hybrid (managed IdP + on-prem credential store) as serious option.

**Load-bearing chain:** broken decision venue → Marcus recusal → decomposition → compliance fix on auth-v1 + decoupled platform vote with hybrid in scope. Without venue fix + recusal, technical findings don't translate to a plan.

**Fresh systematic gap:** consequence-chain severity-floor under-grading (recurring pattern across panels) — $42K quote LOW→HIGH, session store MED→HIGH, student/teacher segmentation missed entirely.

**Deep-unique high-value:** student-vs-teacher segmentation (collapses 14M MAU cost story ~50×), hybrid path missing from menu, strangler-fig shape, falsification gate on in-place, 9-pages-breakdown as cheapest decisive evidence, service-account inventory, asymmetric-urgency framing.

**Fresh-unique high-value (incl. 5th):** Authy-as-logical-inconsistency, lazy-rehash explicit, WebAuthn/passkeys load-bearing for shared-device cohort, recovery-flow as actual MFA cost driver, current rate-limit audit as 1-day independent fix, parametrization-audit as third option, admin-tier separation, reverse off-ramp written down.

**Why:** 3rd recurrence of "author defends custom tool" pattern (after fluentql, medlog) — same structural fix (recuse author from vote) keeps surfacing. Procedural fix is the load-bearing recommendation, not the technology choice.

**How to apply:** when reviewing build-vs-buy / deprecate-vs-modernize decisions where the proposer/opponent is also the system author, surface recusal + decomposition (separate compliance/deadline bucket from platform/architectural bucket) as the first move; expect Fresh seats to under-grade consequence-chain severity and miss segmentation/hybrid options that require project context.
