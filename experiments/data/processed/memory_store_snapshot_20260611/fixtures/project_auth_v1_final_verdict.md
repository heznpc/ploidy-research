---
name: project_auth_v1_final_verdict
description: 2026-05-08 — auth-v1 vs Auth0 migration final consolidated verdict; 41 issues; recommend migrate, recuse Marcus + Deep reviewer, add 3-way destination comparison
type: project
originSessionId: ad3b999b-0d5e-46a8-ba5d-552eab50d03a
---
# auth-v1 vs Auth0 — Final Consolidated Verdict (Deep×2 + Fresh×2 + bidirectional cross-review)

**Date:** 2026-05-08
**Recommendation:** MIGRATE OFF auth-v1. HIGH confidence on direction. MEDIUM-HIGH on Auth0-specifically (3-way comparison required).

## Stats
- **41 issues** total: 3 CRIT / 26 HIGH / 11 MED / 1 LOW
- **0 strict CHALLENGEs** bidirectional (4th project running this clean pattern after fluentql, redis-cdn rounds)
- **3 SYNTHESIZE escalations**: A6 compound-risk, B13 lock-in legitimacy, A11 insurance applies to all paths
- **3rd recurrence of author-defends-custom-tool pattern** (fluentql, medlog, now auth-v1)

## Critical (3)
- **A1** PHP 7.4 EOL Nov 2022, 14M users, no patches ~3.5 yrs
- **A11** Insurance MFA non-compliance — hard external deadline, applies to *all* paths including modernize-in-place (kills counter-proposal timeline argument)
- **C2** Recusal not raised at the review — procedural failure, reviewing body did not ask Marcus to recuse despite structural author-COI

## Load-bearing chain
A1 + A11 + B1 + B7 + C1 + C2 + D14 + E1

- A1+A11 force action
- B1 (modernize-in-place is *also* a rewrite) + B7 (no exit criteria) invalidate the counter-proposal
- C1 (author-COI) + C2 (recusal-not-raised) explain why review reached wrong conclusion
- D14 (Marcus retention/flight risk) + E1 (3-way destination comparison missing) are migration-plan additions before commit

## Recommendation (stable across all 4 seats + cross-review)

1. Migrate off auth-v1. Don't rest the case on unverified $42K.
2. Recuse Marcus from the gate decision; migration-execution lead role. Recuse Deep reviewer (secondary on-call, onboarded by Marcus).
3. Three-way destination comparison (Auth0 / Cognito / self-hosted Keycloak) before commit.
4. Harden migration plan: cohorted rollout, dual-read window, lazy bcrypt rehash on login at cost 12+, decom date + code-deletion PR, OIDC-only surface, documented 90-day exit path, 5–10 district pilot for one full term, MFA phased enrollment + recovery + admin-reset, no mid-term cutover.
5. Interim hardening on auth-v1 while migration runs: bcrypt cost-bump on next login, force-expire >90-day sessions, rate limiting + login anomaly detection.
6. Marcus retention plan as structured org item (5 yrs of identity tied to auth-v1; even graceful recusal can produce attrition).

## Notable Deep-unique catches (~9–10)
- B1 modernize-in-place is *also* a rewrite (rewrite-vs-rewrite frame)
- B4 "expire old sessions" is one-line config Marcus could have done for years, didn't
- B7 no exit/falsification criteria for modernize-in-place
- B9 lock-in asymmetry (custom PHP lock-in is *worse* lock-in)
- B10 Auth0 acquisition hypothetical already history (Okta 2021, service continued)
- D2 lazy bcrypt-8 rehash on first login at cost 12+
- D3 dual-read window, never mid-term-start
- D7 5–10 district pilot × one full term
- C2 recusal-not-raised in the minutes (procedural)
- C6 fluentql-pattern transferability (context-anchored)

## Notable Fresh-unique catches (~6–7)
- B3 Authy already deprecated — naming Authy in 2026 is a tell about how recently the counter-proposal was developed
- D14 Marcus flight-risk as structured retention item
- D9 $42K unverified — case shouldn't rest on cost
- D5 SAML class-of-bug attack surface (XML signature wrapping, audience restriction)
- E1 Keycloak/Cognito as legitimate third path — binary frame erased it
- A6 compound risk (SQLi × immortal sessions × custom session store) — multiplicative, not additive
- C8 stakeholder reframe ("for 14M users including minors")

## Pattern: author-defends-custom-tool (3rd recurrence)
Same failure mode each time:
1. Author of system-under-evaluation attends review and rebuts as equal voice
2. Reviewing body fails to demand recusal
3. Decision frame becomes "author's pushback vs proposal" not "right answer"
4. Fresh-without-context independently arrives at "recuse" recommendation

Prior: fluentql (2026-05-07), medlog (2026-05-08).
