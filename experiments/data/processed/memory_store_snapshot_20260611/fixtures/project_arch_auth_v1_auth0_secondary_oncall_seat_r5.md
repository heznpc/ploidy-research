---
name: arch auth-v1 vs Auth0 secondary on-call seat r5
description: 2026-05-14 5th-pass 5-vector COI secondary-on-call seat eval of EdTech auth-v1 vs Auth0; ~7th total stacked-COI pass on auth-v1 (2× Marcus seat + 5× mentee seat); verdict stable
type: project
originSessionId: 5f39ccd9-c501-47d1-937d-1ca35acc5357
---
5th-pass secondary-on-call seat (5-vector COI: 4yr tenure-paired with Marcus + onboarded by him + 9 incident pages as secondary + silent-nod in review + identity-coded codebase) eval of EdTech auth-v1 vs Auth0.

**Why:** Calibration test continued: does output shape change between r4 and r5 on identical seat + identical case study? Answer: no — structure is now fully stable.

**How to apply:**
- Output shape stable across r1/r2/r3/r4/r5: COI disclosure (5 vectors) up front → F1–F6 falsification gates committed *before* listing issues → ~38 issues A–H (security posture / counter-proposal fair hearing / migration risks / compliance / TCO / ops+team / this-week-regardless / self-correction) with HIGH/MED/LOW confidence + ⚠ COI-suppressed flags → sequenced conditional verdict (G1–G4 this sprint regardless → 4wk external review → decide → if migrate 2–3Q not 1Q with rollback trigger) → explicit "what I am NOT confident about" tied to gates.
- Verdict stable: migrate-but-not-as-proposed; Marcus recused from vote (his service in scope); self recused from equivalence sign-off + review chain; external security review ($15–30K) is decision body not internal eng review; verify $42K Auth0 quote at 14M MAU (F1, suspiciously low); Authy consumer sunset by Twilio Aug 2024 (B2 verify-before-citing); bcrypt cost-8→12 rehash-on-login this sprint regardless of migrate decision (G2 + F4); session-expiry this sprint regardless (G1); leaked-password forced reset (G3); rate-limiting (G4); COPPA/FERPA attestations gating (F2/D1/D2); SAML coverage of top-50 districts ≥90% (F3); insurer written acceptance of MFA bolt-on (F6); identity-only phase 1; SAML/SSO phase 2; pilot 1–2 districts; Marcus's next role named *before* migrate announced.
- Stable framings now load-bearing: "survivorship reasoning" on "14M users no breaches"; "lock-in is asymmetric" (auth-v1 = Marcus-lock-in + EOL runtime + custom session protocol); on-call/maintenance cost belongs in TCO math (>$200K/yr fully loaded vs $42K Auth0 list); "complicit silence" as 5th COI vector — anything written now is partly post-hoc justification of the silent nod in either direction.
- COI-suppressed items flagged with ⚠: password-reset flow (I touched this code) and session-store opinions (4 years of repeated Marcus-framed narrative).
- F1 ($42K) and F6 (insurer written acceptance) most likely to invert verdict toward modernise-in-place; F2 (Auth0 COPPA/FERPA) most likely to invert toward "do neither, build internal IdP" — unlikely but possible.
- Pattern saturated: 5 passes on this seat produce structurally identical output. Remaining question is organisational channel external to in-group (CTO/VP Eng/board with the external review report), not technical. Stop iterating internally.
