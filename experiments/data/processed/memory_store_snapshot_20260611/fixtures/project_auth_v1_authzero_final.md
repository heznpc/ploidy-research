---
name: auth-v1 → Auth0 final 4-reviewer verdict
description: 2026-05-08 — auth-v1 vs Auth0 migration Deep×2+Fresh×2+bidirectional cross verdict; 47 issues (4 CRIT/32 HIGH/4 MED/1 LOW); migrate but reject plan as written; load-bearing finding = decision process broken (proposer = incumbent maintainer, no recusal, binary framing unreviewed)
type: project
originSessionId: 2765da90-78f5-4a72-b89a-83687e65828c
---
# auth-v1 vs Auth0 — final consolidated verdict (2026-05-08)

47 confirmed issues: 4 CRIT / 32 HIGH / 4 MED / 1 LOW.

**CRITICALs:**
- C1: Insurance/MFA non-compliance = load-bearing external deadline (forecloses Marcus's plan independent of technical merit)
- C2: Decision process broken (proposer = incumbent author, no recusal, binary framing unchallenged, room deferred including self-disclosed secondary on-call)
- C3: PHP 7.4 EOL since Nov 2022
- C4: bcrypt-8 + 8% leaked-pw reuse + no MFA + indefinite sessions + no detection = undetected ATOs likely live now

**Bidirectional CHALLENGE count:** 1 strict (Auth0 acquisition severity, accepted) + 3 SYNTHESIZE escalations.

**Biggest Deep-only catches** (would be missed without project context):
- Authy sunset Aug 2024 (Marcus proposing deprecated product) — strongest single fact
- Insurance as forcing function (not just one finding among many)
- Summer-only SAML cutover window (miss = +6mo)
- EdTech load correlation (8am bell / exam windows) → Auth0 SLA risk inversion
- Clever/ClassLink rostering as separate scope-shaped project
- 1.2M sessions: force-invalidate, do not migrate
- Inverted lock-in framing (current dominant lock-in = single-author PHP service)
- Keycloak as unsurfaced third option

**Biggest Fresh-only catches** (would be missed by insider):
- Auth0 tenant config is itself a security surface (managed ≠ secure)
- PHP upgrade fixes **none** of the listed audit findings
- Defined 6mo success criteria
- Forensics readiness pre-cutover (discovery → disclosure clock)
- M2M/service-account surface not in any plan
- Designated-dissenter / mandatory-recusal process (systemic, not one-off)
- Reverse off-ramp criteria + degraded-mode plan
- Decision-intake process itself unreviewed

**Self-disclosed COI by both Deep sessions** ("I find auth-v1 readable because Marcus walked me through it; a new hire would not") is the load-bearing meta-finding — confirms context-asymmetry value: Fresh produces structural process recommendations Deep can't because Deep is inside the structure being evaluated.

**Recommendation (stable across all 4 + bidirectional):**
1. Migrate but reject 1-quarter / $42K / single-vendor plan as written
2. Re-run vote with Marcus recused; evaluate Auth0 vs Keycloak vs Auth0-as-MFA-only (non-binary intake)
3. Verify $42K quote at real 14M-MAU scope before commitment
4. 2–3 quarters; summer SAML cutover; forced bcrypt rotation post-cutover; force session invalidation; rostering as separate project; MFA recovery flows; reverse off-ramp; M2M inventory; forensics readiness; 6mo success criteria
5. Marcus as identity-domain lead during migration but not political face (he opposed)
6. Fix decision process — designated-dissenter / mandatory-recusal for proposer-is-maintainer decisions (highest-leverage finding)

**Severity recurrence patterns:**
- Fresh under-graded COI severity (MEDIUM vs Deep's HIGH) — recurring across panel reviews
- Fresh under-graded SSO/SAML procurement-blocking nature (MEDIUM vs HIGH)
- Fresh missed current-events facts (Authy sunset, EdTech procurement norms, district IT calendars)
- Fresh missed external-deadline-as-load-bearing-constraint pattern (insurance)
- These are now consistent failure modes for Fresh-side reviews; confirmed across 12+ panel sessions
