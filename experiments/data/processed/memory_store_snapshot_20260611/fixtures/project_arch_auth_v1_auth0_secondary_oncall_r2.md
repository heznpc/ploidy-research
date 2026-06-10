---
name: arch auth-v1 vs Auth0 — secondary-on-call seat, 2nd pass
description: 2026-05-14 2nd-pass eval of EdTech auth-v1 vs Auth0 from secondary-on-call 5-vector COI seat; verdict + recusal stable, F3 Authy-sunset noted as verify-before-citing
type: project
originSessionId: 150bb5a5-7c6d-4d31-92cd-1c9cbf55de2b
---
2026-05-14: 2nd run of auth-v1 vs Auth0 case from the secondary-on-call seat (5-vector COI: mentee of Marcus, 9 pages over 12mo, 4yr/5yr paired tenure, silent in review, codebase identity).

Structure: COI declared up front, 6 falsification gates committed before listing issues, ~30 issues across A–G, verdict + 8-step structural fix.

Verdict stable across both passes from this seat: **migrate to Auth0** subject to F1–F6, **recuse Marcus from decision** (retain as SME for cutover), verify $42K quote, scope to identity-only in v1, ship MFA in-place as 6-8 week hedge for insurance renewal independent of migration, force-reset 8% leaked-password cohort, document exit via adapter pattern, sequence cutover by district with rollback metric, build secondary-on-call rotation regardless.

**New / load-bearing this pass**:
- F3 (Authy MFA path) flagged with explicit verify-before-citing: prior memory says Authy app sunset Aug 2024; did not re-verify in-session; substitute Twilio Verify API or other TOTP provider if confirmed dead.
- G2 reframes lock-in: current lock-in = one person + EOL PHP + hand-rolled crypto; Auth0 lock-in is escapable via thin adapter to alt IdP (Cognito, WorkOS, Keycloak). Person-lock-in is the harder one.
- F1 hedge: ship MFA in-place in 6-8 weeks *independent* of migration timeline as insurance-renewal hedge, then migrate at calmer pace.

**Why**: 6th stacked-COI case (after saas-cells, arch-split, medlog, auth-v1 round 1, secondary-on-call round 1). Confirms the pattern: declared COI + falsification gates up front + recusal of the load-bearing author + technical SME role retained = stable verdict across re-runs.

**How to apply**: When the user re-runs the same case from the same COI seat, prior memory's verdict should hold; the new value is (a) catching anything that decayed (Authy sunset), (b) tightening the structural fix (insurance-MFA hedge is independent of migration timeline), (c) recording confidence calibration. Stop iterating after ~2 passes from same seat — remaining question is organisational not technical.
