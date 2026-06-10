---
name: auth-v1 → Auth0 Deep×2 → Fresh×2 cross-review
description: 2026-05-08 auth-v1 deprecation panel — Deep×2 cross-reviewing Fresh×2; 0 CHALLENGE, 3 severity escalations, 12 Fresh-unique load-bearing items including $42K unverified + missing third-path (Keycloak) + Marcus-flight-risk
type: project
originSessionId: f4b45524-b4c6-4ab9-bf6e-aca14c391015
---
Auth-v1 → Auth0 deprecation review, 2026-05-08. Deep×2 (full project context, both with Marcus COI declared) cross-reviewing Fresh×2 (no project context).

**Verdict stable across all 4 sessions: migrate to Auth0, recuse Marcus from gate, harden plan.**

**Why:** Status quo accumulates compliance/security/bus-factor risk faster than migration risks; insurance non-renewal is hard external deadline; Marcus's "modernize in place" is also a rewrite with same single-author + custom-code-SQLi-rate problems preserved.

**How to apply:** When reviewing similar deprecation/migration debates where the proposer is the system author:
- Demand recusal from gate vote, not just disclosure
- Restore third-path comparison Marcus-style binary frames erased
- Verify vendor cost figures (Deep accepted $42K; Fresh independently flagged it as too-low for 14M MAU + SAML + MFA)
- Require falsification criteria / exit criteria for "modernize in place" plans

## Cross-review pattern (matches fluentql + medlog)

3rd recurrence in this project of author-defends-custom-tool pattern:
1. fluentql (10 rounds, 2026-05-07)
2. medlog (2026-05-08)
3. auth-v1 (this review, 2026-05-08)

All three: author of system proposes alternative to deprecation; review fails to demand recusal; Deep+Fresh both arrive at same recusal recommendation; Fresh consistently catches plan-quality gaps Deep accepts at face value due to relational anchoring.

## Fresh-unique load-bearing items (12)

1. **$42K vendor pricing unverified** (F1-13) — Deep accepted; Fresh flagged Auth0 list pricing at 14M MAU + SAML + MFA does not pencil
2. **Authy deprecated 2024 → in-place plan wasn't researched recently** (F1, F2-10)
3. **Third path missing** — Keycloak/Ory/Cognito; Marcus's binary frame survived
4. **Interim hardening WHILE migration runs** (F1-Rec-5): force-expire >90d sessions, bcrypt-on-login bump, accelerate PHP patch
5. **Marcus flight-risk as structured item** (F1-Rec-6): 5yr identity tied to auth-v1, deprecation = identity threat
6. **"Expire old sessions" is one-line config he could have done years ago** (F2-11) — counter-proposal as reactive defense
7. **No SSO/SAML in counter-proposal** (F2-12) — permanent maintenance tax + procurement blocker
8. **Counter-proposal is wish list not plan** (F2-13)
9. **SQLi as complete-compromise primitive** (F2-3) — sharpest framing across panel
10. **Long-tail decom commit + code-deletion PR** (F2-24)
11. **Vendor-failure mitigation IN plan to defang Marcus** (F2-25)
12. **Falsification criteria for "modernize in place"** (F2-16) — else runs indefinitely

## Deep-unique items Fresh missed (9)

1. Recusal-not-raised in review minutes (procedural)
2. Code-review authority asymmetry — Marcus blocks migration PRs even if gate goes to migrate
3. 4-year colleague silence as institutional pattern
4. Shared 9 incident pages normalizes fragility
5. Lock-in asymmetry concrete evidence (Auth0 has export tooling; custom PHP has none)
6. Dual-read window for session cutover (specific architecture)
7. Pilot scope = one full term, not half-term
8. Auth0 acquired by Okta 2021, service continued — counter-evidence to Marcus's hypothetical
9. Symmetric person-quarters quantification demand for both paths

## Severity escalations (3)

- F1-8 author-COI: MED → HIGH (load-bearing governance defect, recurring pattern)
- F1-11 1-quarter timeline: MED → HIGH (district SAML long-tail alone is multi-quarter)
- F2-6 "no breaches" survivor bias: MED-HIGH → HIGH (5yr auth for minors)

## 0 strict CHALLENGEs

Both directions across panel — pattern matches fluentql/redis-cdn convergence behavior. Deep+Fresh agree on substance; differ only on completeness (Fresh catches plan-quality gaps; Deep catches procedural/historical gaps).

## Round 2 (2026-05-08, same day) — second Deep×2 → Fresh×2 pass

Same panel composition, fresh sessions. Confirms convergence stability.

**0 strict CHALLENGEs again.** **7 severity escalations** (Fresh under-grades governance/scope items):
- SAML districts MED → HIGH (procurement gate)
- Path-B COI MED → HIGH ×2 (both Fresh seats)
- Bus factor MED → HIGH
- 1-quarter timeline MED → HIGH (unscoped)
- District SAML multi-party MED → HIGH
- $42K cost framing LOW → HIGH (load-bearing arithmetic error in Marcus's comparison)

**Fresh-unique sharpenings adopted (4):**
1. "Reassign Marcus as migration tech-lead" — positive role split, lower face-saving cost than vote-recusal alone
2. Open-questions discipline (detection inventory? distinct district IdP count?)
3. $42K-as-license-only with both-sides-of-comparison understated (build AND buy)
4. "Demonstrated org execution rate" framing — build-path feasible technically but not at this team's track record

**Deep-only catches still missed by Fresh (8):** silence-as-not-consent procedural fix, falsification criterion for in-place, hybrid A8 (Auth0 front + owned credential store), lazy-rehash-to-argon2id at cutover, bcrypt-8-as-meta-on-org, MySQL session store hot-path liability at 8am login spike, reverse off-ramp + falsification, self-flag-as-data.

**Pattern note:** Fresh systematically under-grades consequence-chain + governance items; grades artefact-level security correctly. 4th recurrence in project memory (fluentql, medlog, redis-cdn, now auth-v1 ×2).
