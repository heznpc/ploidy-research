---
name: auth-v1 vs Auth0 final verdict
description: 2026-05-08 — auth-v1 deprecation Deep×2+Fresh×2 final consolidated verdict; 45 issues (2 CRIT/27 HIGH/16 MED); VACATE review + MIGRATE with conditions
type: project
originSessionId: 155893db-0858-4db4-8626-d2b46af8f938
---
2026-05-08 — auth-v1 vs Auth0 migration final verdict after Deep×2 + Fresh×2 + bidirectional cross-review.

**45 confirmed issues (2 CRIT / 27 HIGH / 16 MED / 0 LOW). 0 bidirectional CHALLENGEs. 6 SYNTHESIZEs.**

**Why:** Project context: Marcus = auth-v1 author + primary on-call + Deep reviewer's mentor; Deep is secondary on-call with 9 page-debts; review held with author voting + Deep silent. 14M minors. Insurance MFA flag = renewal-gate.

**How to apply:**
- Direction-convergence (migrate, not modernize-in-place) is unanimous 4/4, derivable from spec alone.
- Decision-mechanism (vacate the current review) is Deep-only — not derivable from spec; requires knowing the suppression structure.
- Load-bearing CRITICAL pair: #38 procedural invalidity + #41 mentor/on-call suppression mechanism. Without both, the rest reads as a tech list.
- Fresh-unique adoptions: $42K likely 2–5× undercount (Auth0 enterprise MAU); COPPA under-13 flows missing from plan; school-calendar cutover timing; single-district pilot.
- Deep-unique catches: Authy discontinued Aug 2024 (calendar); Keycloak/Ory absent from option set; in-place 2 eng-quarters > $42K; custom SAML XSW class; "no breaches" = survivorship without telemetry; PHP 7.4→8.3 is itself 1–2mo migration.
- Recommendation: vacate → ship MFA/breach-list/TTL in parallel regardless of platform → external pentest + real Auth0 enterprise quote → re-frame as 3-way (Auth0 vs Keycloak vs hardened in-place) → re-vote with Marcus recused, kept as SME not impl-lead.

**Pattern:** 2nd recurrence of severity-floor under-grading by Fresh on consequence-chain items (procedural invalidity treated as "weight less" not "vacate"; in-place economics not flipped). 1st recurrence of Deep-unique structural-silencer catch (mentor + on-call + no recusal protocol = predictable suppression).
