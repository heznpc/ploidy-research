---
name: arch auth-v1 vs Auth0 secondary on-call seat r4
description: 2026-05-14 4th-pass 5-vector COI secondary-on-call seat eval of EdTech auth-v1 vs Auth0; ~44th stacked-COI case overall / 9th domain; verdict stable across r1/r2/r3/r4
type: project
originSessionId: cc533c3b-fdff-4825-8dcc-61759d4e7cc1
---
4th-pass secondary-on-call seat (5-vector COI: 4yr tenure-paired with Marcus + onboarded by him + 9 incident pages as secondary + silent-nod in review + identity-coded codebase) eval of EdTech auth-v1 vs Auth0.

**Why:** Now 6 distinct stacked-COI passes on the auth-v1 proposal (2× authorial Marcus seat + 4× mentee secondary-on-call seat). ~44 stacked-COI cases overall across 9 domains. Calibration test: does the output shape change between r3 and r4 on identical seat + identical case study?

**How to apply:**
- Output structure stable: COI disclosure (5 vectors) → F1–F6 falsification gates committed up front → ~35 issues A–E (security / operational-structural / Marcus-plan / Auth0-migration-risks / governance) with HIGH/MED/LOW + ⚠ COI-suppressed tags → conditional verdict → explicit "what I am NOT confident about" tied to gates.
- Verdict stable: migrate-but-not-as-proposed; recuse Marcus + recuse self; external auth review ~$15–30K *before* contracts; verify $42K quote (F1); verify Twilio-Verify-vs-discontinued-Authy-app (F5); confirm COPPA/FERPA attestations (F6); confirm insurer's written position on in-place MFA (F3); confirm staffability without Marcus (F4); audit Auth0 CVE history (F2); identity-only phase 1; SAML/SSO phase 2; pilot 1–2 districts; parallel minimum in-place remediation; per-phase rollback documented.
- Distinct new framings this round vs r1–r3:
  - "Survivorship reasoning" name for Marcus's "no breaches" framing (B3) — absence of detected breach ≠ absence of breach, especially given audit-log gaps (A9).
  - "Lock-in is asymmetric" — auth-v1 is also lock-in (custom session protocol + custom password flow + EOL runtime + single author). Re-frames Marcus's strongest argument as not unique to Auth0.
  - "On-call cost belongs in the $42K math" (B4) — status quo isn't free.
  - "Complicit silence" (5th COI vector) explicitly anchored: anything I say now is partly motivated to retroactively justify the silent nod, in either direction.
- Items where I am structurally COI-suppressed: A8 (password-reset flow — I worked on this code, motivated to assume it's fine). Tagged ⚠ to flag the bias.
- F1 ($42K) and F3 (insurer written acceptance) are the gates most likely to invert verdict. F2/F5/F6 most likely to confirm migrate.
- Pattern saturated: 4 passes on this seat produce structurally identical output. Remaining question is organisational channel external to in-group (CTO/VP Eng/board with the external review report), not technical. Stop iterating internally.
