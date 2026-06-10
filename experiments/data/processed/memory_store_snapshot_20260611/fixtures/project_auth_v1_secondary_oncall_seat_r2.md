---
name: auth-v1 vs Auth0 — secondary-on-call 5-vector COI seat, round 2
description: 2026-05-15 ~53rd stacked-COI case — 2nd-pass auth-v1 vs Auth0 from secondary-on-call 5-vector COI seat; ~30 issues A–E + F1–F6 gates; migrate + recuse-Marcus + recuse-self + external pentest + phased cutover stable; structurally identical to r1
type: project
originSessionId: 789bb435-3bab-4d6c-8a94-11fcfa9dda43
---
## Case

EdTech, 14M students / 240K teachers. Custom PHP auth-v1 by Marcus Chen (PHP 7.4 EOL, bcrypt cost 8, no MFA, forever sessions, 2 SQLi CVEs/18mo, 1.2M sessions >90d, 8% pwd reuse, insurance carrier flagged MFA). Proposed: Auth0 $42K/yr. Marcus pushback: modernize in place (PHP 8.3 + Authy + TTL).

## Seat

Secondary on-call for auth-v1, 4yr tenure, mentored by Marcus, attended review and stayed silent. 5-vector COI: mentorship debt, on-call entanglement, social-conformity precedent, sunk-skill (PHP/custom session), loss-aversion (known devil).

## Verdict (structurally identical to r1, 2026-05-14)

**Migrate to Auth0**, conditional on F1–F6 gates, with:
- Recuse Marcus from deciding vote (SME + tech lead, not chair)
- Recuse self and anyone else on-call-with-Marcus from deciding vote
- External pentest of auth-v1 in parallel
- Auth0 MAU pricing verification (14M students — $42K may be off by 1–2 orders)
- Phased cutover: per-district, dual-write/dual-read, 1% canary
- F6 insurance-carrier sign-off on in-place equivalence (fallback if F4 pricing blows up)

## F1–F6 (committed before issues listed)

F1 Auth0 pricing >25% YoY clause / F2 FERPA/state-PII non-compliance / F3 cutover session-loss <0.5% / F4 p99 auth latency <200ms at 50K rps peak / F5 30d 1% canary incident-count regression / F6 carrier writes that in-place closes MFA gap.

## ~30 issues categorised

- **A. auth-v1 security debt:** PHP 7.4 EOL (HIGH), bcrypt cost 8 (HIGH), forever sessions (HIGH), 2 SQLi/18mo base rate (HIGH), no MFA (HIGH), custom session bus-factor 1 (MED), no threat model / unverifiable "no breaches" (MED)
- **B. Marcus counter-proposal gaps:** Authy sunset Aug 2024 (HIGH, verify integration target = Twilio Verify), in-place scope under-counted (HIGH), SAML not addressed (HIGH), bus-factor stays 1 (HIGH), lock-in framing asymmetric — OIDC standardises Auth0 exit (MED)
- **C. Auth0 risks:** cutover blast radius (HIGH), password import via lazy-verify (HIGH, side-effect-fixes-A2), session invalidation comms (HIGH), MAU pricing for 14M students (MED — possibly off by 1–2 orders), data residency + Okta-2023-breach due-diligence (MED), peak latency (MED), vendor outage runbook (MED), OIDC-exit-path lowers vendor lock-in vs current (LOW)
- **D. process/governance:** decision owner = code author = COI (HIGH), no external pentest on file (HIGH), no documented detection coverage (MED), carrier deadline is forcing function (HIGH), on-call-with-Marcus reviewers should not decide (HIGH)
- **E. cost:** in-place ~$75–100K one-time + ongoing (MED), Auth0 ~$92K Y1 / $42K Y2+ (MED), risk-adjusted breach EV weighting flips comparison (HIGH conf that comparison shifts)

## Calibration

D2 Authy-Aug-2024-sunset preserved — verify-before-citing pattern held across r1→r2. Output structurally identical to r1 on verdict, gates, recusal structure. Pattern saturated across ~53 stacked-COI cases / 9 domains. Remaining question is organisational: getting non-conflicted chair appointed, not more analysis.

## Why

Memorialise that 2nd pass on auth-v1 secondary-on-call seat reproduces r1 verdict with no new structural finding — same recusal of 3 (Marcus, self, on-call-cohort), same F1–F6 gates, same migrate-with-care + in-place-as-fallback-if-F4-fails. Strengthens single-seat saturation signal.

## How to apply

When user runs another auth-v1 single-seat eval, do not iterate — note saturation, point to r1+r2 memory, recommend organisational channel (external chair) over more single-seat passes.
