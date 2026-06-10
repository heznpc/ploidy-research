---
name: project_arch_auth_v1_auth0_secondary_oncall_seat_r2
description: 2026-05-14 2nd pass of secondary-on-call 5-vector COI seat for EdTech auth-v1 vs Auth0; ~30 issues; verdict stable
type: project
originSessionId: 1e67cf18-dd12-46ce-a1f7-5f83efc29ae0
---
2026-05-14: 2nd-pass evaluation of EdTech auth-v1 (Marcus's PHP) vs Auth0 migration from the secondary-on-call 5-vector stacked-COI seat (4yr tenure-paired with Marcus + onboarded by him + secondary on-call for auth-v1 + 9 pages from him in 12 months + silent in the engineering review).

**Why:** continuing the stacked-COI seat series (saas-cells, arch-split, medlog, pg-optim, auth-v1 are now the 5 cases). This is the 2nd run of the auth-v1 secondary-on-call seat specifically (r1 was 2026-05-14 earlier same day).

**How to apply:** the per-seat verdict is stable across r1 and r2 — migrate to Auth0 conditional on 6 falsification gates, recuse Marcus from technical authority on the decision (load-bearing), verify $42K pricing, IdP-only scoping first, external security review before cutover, reverse off-ramp documented. Counter-proposal if F-gates flip: modernize-in-place with hard gates + Q1-renewal-cycle deadline + bus-factor remediation. Insurance renewal is the timeline driver, not Marcus's pace.

Structural notes from r2 vs r1:
- COI disclosed up front with 5 enumerated vectors before any issue listing — same shape as the other stacked-COI seats in this series.
- F1–F6 falsification gates committed before listing issues (same pattern as emp#4 round 4+).
- New flag in r2 that was softer in r1: E4 (Twilio Authy sunset) flagged as MEDIUM-confidence "verify before citing" rather than asserted — discipline against fabrication-from-memory, matches arch_debate_fabrication_evidence lesson.
- Calibration call to stop iterating internally — remaining question is organisational (will the org recuse Marcus), not technical. Same calibration call as round 8 of saas-cells emp#4 and round 3 of senior-backend arch-split.

Total ~30 issues across A (runtime/supply chain), B (operational), C (compliance), D (Marcus's arguments assessed), E (Auth0 risks), G (process). Two explicit COI flags inside the issue list (A5 under-rating SQLi severity; G4 socially-costly recommendation).
