---
name: auth-v1 vs Auth0 — secondary-on-call mentored seat
description: 2026-05-14: 5-vector COI seat (mentee + secondary on-call + 9 pages received + silent in review + codebase identity); ~30 issues across A–D + 6 falsification gates; migrate + recuse-Marcus + verify-$42K + IdP-only scoping + insurer-deadline stable; 5th stacked-COI case after saas-cells / arch-split / medlog / auth-v1-author-COI
type: project
originSessionId: 76fae374-e693-42fc-b792-3462df79740c
---
EdTech auth-v1 (PHP 7.4 EOL, bcrypt cost 8, no MFA, no session rotation, 2 SQLi CVEs in 18mo, 1.2M >90-day sessions, 8% leaked-password reuse, insurer flagged) vs Auth0 migration ($42K/yr claimed, 1 quarter).

**Why this seat is distinct from prior auth-v1-author-COI eval:**
Prior eval was a 5-vector COI on the author position (Marcus). This one is the *mentee/secondary-on-call* position — 4yr tenure, 9 pages answered by Marcus, onboarded by him, attended review and nodded silently, identity tied to auth-v1 codebase. Tests whether stacked-COI structure holds when COI is *socially downstream* rather than *authorial*.

**How to apply:**
- Verdict held: migrate + recuse-Marcus + verify $42K + identity-only first phase + pilot 1–2 districts + minimum in-place remediation in parallel + insurer-renewal deadline.
- New element vs prior eval: "complicit silence" as 5th COI vector — being in the room and not speaking is itself a bias I am motivated to retroactively justify.
- Falsification gates committed up front: F1 (SAML/Clever fit), F2 ($42K verification), F3 (insurer accepts in-place), F4 (in-place staffable <1Q), F5 (Auth0 RCE history), F6 (no enterprise-discount path).
- Auth0 list price at 14M MAU is publicly unconfirmed; $42K figure flagged as suspicious without invoice.
- "Authy" reference in Marcus's plan flagged: Twilio shut down standalone Authy consumer apps 2024 → tell about freshness of in-place plan.
- "Lock-in" framing rebutted as asymmetric: auth-v1 is also lock-in (single author, EOL runtime, custom session protocol).
- D1 = author recusal load-bearing; D2 = senior pushback deterring dissent flagged as process issue; D3 = insurer signal is a deadline not a risk.
- Calibration: now 5 distinct stacked-COI seats across different proposals (saas-cells, arch-split, medlog, auth-v1-author, auth-v1-mentee) → COI-seat structure is the stable artefact, not the specific issue lists.
- Pattern reproducing: falsification gates up front + COI disclosure up front + recusal recommendation + counter-proposal-with-conditions = stable verdict structure across all 5 seats.
