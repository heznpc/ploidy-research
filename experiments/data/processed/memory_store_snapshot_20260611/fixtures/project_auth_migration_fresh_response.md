---
name: auth migration Fresh×2 → Deep×2 cross-review
description: Fresh-side cross-review of Deep×2 on auth-v1 vs Auth0 migration; 0 CHALLENGE, ~80% overlap, Fresh-unique catches and Deep-unique escalations identified
type: project
originSessionId: 479a6485-77b4-41dc-a623-365ae50caf83
---
2026-05-08: Fresh×2 → Deep×2 cross-review on auth-v1 vs Auth0 migration decision.

**Bidirectional pattern: 0 strict CHALLENGEs.** Both sides converge on direction (migrate with conditions), root cause (governance failure + concurrent technical defects), and load-bearing observation (review procedurally invalid due to author-as-voter + on-call silence).

**Fresh-unique catches Deep under-weighted:**
- Auth0 MAU pricing math at scale ($42K likely 2–5× undercount for 14M+240K)
- Under-13 student auth flows distinct from generic COPPA flag (Auth0 default flows assume adult users)
- Force-rehash on login required to retire cost-8 bcrypt — not implicit in lazy migration
- School-calendar comms constraint (avoid finals, start-of-term)
- Pilot with single district as validation gate before full cutover
- Reassign Marcus to lead migration (expertise asset, ownership risk to manage) — sharper than Deep's "recuse from impl lead"

**Deep-unique catches Fresh missed:**
- Authy discontinued Aug 2024 → Twilio Verify (proposal references nonexistent product) — CRITICAL falsification
- Option set artificially narrowed (Keycloak/Ory/Cognito/Firebase missed) — reframes whole debate
- Cookie hardening audit gap (Secure/HttpOnly/SameSite/CSRF binding)
- SAML XSW class of vuln in hand-rolled PHP SP
- Structural-silence-as-finding (on-call mentee suppression)
- In-place economics inverted: 2 eng-quarters @ $50–80K each > $42K Auth0 quote
- Okta-acquired-Auth0-in-2021-without-harm empirically falsifies "what-if-acquired" hypothetical
- PHP 7.4→8.3 not a bump (1–2mo on its own)
- No pentest budget named for in-place option

**Severity-floor pattern reproduced.** Fresh under-graded: 19,200 active-risk accounts (collapsed under no-MFA), procedural invalidity (treated as weight-his-input-less rather than vacate-the-review), inverted in-place economics.

**Load-bearing chain:** governance (D2-26 author-as-voter + D2-33 silence-as-finding) + technical (PHP EOL + bcrypt cost-8 + immortal sessions + no MFA + SQLi pattern + no detection signal) + economics (D2-15 inverted in-place cost) + premise refutation (D2-12 Authy discontinued + D2-18 Okta acquisition harmless). Counter-recommendation: vacate current decision, external pentest, reframe as 3-way (Auth0 vs Keycloak vs hardened in-place), MFA + breach-list + session TTL ship in parallel regardless of platform choice.

**Why:** This is the 8th+ recurrence in the panel of the "author defends own tool" governance pattern (cf. fluentql, medlog, redis-cdn). The Authy-discontinued catch is a new failure mode: proposal references a product that no longer exists, which Fresh cannot detect without external knowledge anchoring.

**How to apply:** When evaluating deprecation/migration debates where the system author participates: recusal-or-abstention is procedural baseline, not a critique. Verify all named third-party products still exist. Always check for narrowed option set (build-vs-buy is usually a false dichotomy when self-hosted FOSS exists).
