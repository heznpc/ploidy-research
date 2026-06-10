---
name: arch auth-v1 vs Auth0 secondary on-call seat r3
description: 2026-05-14 3rd-pass 5-vector COI secondary-on-call seat eval of EdTech auth-v1 vs Auth0; ~41st stacked-COI case
type: project
originSessionId: 0e75a278-3006-482c-b010-8856dbf20ad8
---
3rd-pass secondary-on-call seat (5-vector COI: 4yr tenure-paired with Marcus + onboarded by him + 9 incident pages as 2ndary + silent-in-review nod + identity-coded codebase) eval of EdTech auth-v1 vs Auth0 migration.

**Why:** ~41st stacked-COI case in this thread across ~9 domains (SaaS-cells, PG-optim, arch-split, medlog/OTel, CDN/Redis, auth-v1/Auth0, logistics migration, etc.). Pattern saturated; r1 and r2 already exist for this exact seat earlier 2026-05-14.

**How to apply:** Output shape now fully stabilised across 3 passes of this seat — COI disclosure up front (5 vectors named), F1–F6 falsification gates committed *before* listing issues, ~35 issues grouped A–H (A security / B compliance / C operational on-call / D in-place-plan-risk / E Auth0-risk / F migration mechanics / G governance / H self-correction what-I'm-probably-wrong-about), explicit HIGH/MED/LOW per item. Verdict stable across r1/r2/r3: migrate-but-not-as-proposed conditional on gates; recuse-Marcus + recuse-self + external-security-review + insurance-and-counsel-written-positions + verify-$42K-quote + verify-Authy-sunset-before-citing + IdP-only-scope-cut + 2Q-phased + bcrypt-rehash-on-login-now-regardless. Section H (self-correction) is new vs r1/r2 — flags own COI-induced underweighting of Auth0 lock-in and overweighting of bus-factor-1.

Stable items across all 3 passes: Marcus author-COI recusal load-bearing; insurance renewal cycle is timeline driver (not Marcus's pace); $42K likely 5–10× wrong-low; Authy/Twilio sunset must be verified-before-citing (memory rule); 2 SQLi CVEs in 18mo + PHP 7.4 EOL + bcrypt cost 8 + 1.2M >90d sessions + no MFA is structurally unfixable inside the in-place plan because the same author writes the fix. Remaining Q is organisational channel external to in-group (CTO / VP Eng / board), not technical. F1 ($42K real?) + F3 (counsel) most likely to invert; F2/F5/F6 most likely to fail and confirm migrate.
