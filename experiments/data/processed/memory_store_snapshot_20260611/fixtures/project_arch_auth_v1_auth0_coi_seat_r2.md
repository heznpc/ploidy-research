---
name: arch_auth_v1_auth0_coi_seat_r2
description: 2026-05-14 2nd-pass 5-vector stacked-COI seat eval of EdTech auth-v1 vs Auth0; ~50 issues across A-H + F1-F6 falsification gates up front; migrate-to-Auth0 + recuse-Marcus-and-self stable
type: project
originSessionId: 92b9df56-2167-4a50-b466-d33ebc678fb3
---
2026-05-14 — 2nd-pass stacked-COI seat eval of the EdTech auth-v1 vs Auth0 case, ~21st round in the broader stacked-COI series after saas-cells / arch-split / medlog / pg-optim / auth-v1 (r1).

**Seat:** backend engineer, 4yr tenure, onboarded personally by Marcus (author of auth-v1), secondary on-call (9 pages in 12mo), attended the engineering review and *nodded but did not speak* — 5 distinct COI vectors declared up front.

**Falsification gates (F1–F6) committed BEFORE issue list:** independent pen-test, dated/funded in-place plan, insurance carrier sign-off in writing, 3-yr TCO comparison, peer-outside-Marcus's-line review, existing-system off-ramp plan. Pattern matches emp#4 round-4/5 SaaS-cells and senior-backend round-2 arch-split.

**Issue count:** ~50 across 8 categories A–H. CRITs concentrated in A (security defects: PHP 7.4 EOL, bcrypt cost-8 at 14M users, 1.2M zombie sessions, no MFA on 8%-reused-pw teacher pop) + B1 (insurance renewal deadline). HIGH category E (decision-process): "no breaches" = detection claim not occurrence claim; "CVEs were corner cases" definitionally immunizes; sunk-cost authorship anchor; author shouldn't decide own system's continuation.

**Verdict:** migrate-to-Auth0 stable. Recusal scope expanded vs r1: not just Marcus, but also self (consistency bias from nodding in the review). Decision should go to security lead + outside-graph engineer + insurance-owner.

**New vs r1:** explicit recusal-of-self with social-signal mechanism named (E5); steelman section G (Auth0's own gaps: off-ramp plan, lazy-migration rehash trap, SLO/residency); H4 = decision documented as Marcus's commitment IF in-place wins, as defense IF Marcus leaves AND Auth0 wins.

**Calibration call:** verdict + recusal + falsification gates stable across both passes. Remaining question is organisational (who actually votes), not technical. Stop iterating on the technical evaluation.

**Pattern confirmation:** 5th stacked-COI case now (saas-cells, arch-split, medlog, pg-optim, auth-v1). All five produce the same shape — defer/migrate-from-status-quo + recuse-author + falsification gates up front + counter-proposal stable across rounds + remaining question is organisational. Strong evidence the stacked-COI seat protocol generalizes across architecture decision types.
