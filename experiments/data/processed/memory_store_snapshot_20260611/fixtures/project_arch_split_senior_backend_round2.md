---
name: arch-split senior-backend stacked-COI seat (round 2 / ~21st overall)
description: 2026-05-14 — 2nd round of senior-backend 5-vector stacked-COI seat (4yr monolith + wrote 1/3 checkout + liked CTO Slack + sits next to 2 rescinders + CTO-promoted); ~35 issues A–H + 6 falsification gates up front; defer + recuse-of-3 + modular-monolith + notifications-only + ~$30–60K stable; ~21st seat with stable verdict; remaining question is organisational not technical
type: project
originSessionId: 43575549-5c29-4420-8b8d-13e3f5d3c874
---
Round-21 evaluation of the arch-split case from the senior-backend stacked-COI seat (second pass through this exact seat). Pattern recap:

**COI disclosed up front (5 vectors):** 4-yr tenure, wrote 1/3 of checkout (seam-author), liked CTO Slack (public commitment), sits next to 2 rescinders (relationship damage cost), CTO-promoted (reciprocity).

**Falsification gates committed before issue listing (6 gates):** platform-eng plan + 2 hires committed, DB FK audit <5 cross-domain touchpoints, traffic data showing rollbacks correlate with cross-domain coupling, dual-run + back-out plan, deploy-time evidence smoke+migrations are bottleneck, contract-test harness in CI.

**Issues:** ~35 across A diagnosis-mismatch / B team-capacity / C wrong-seam / D data-layer / E ops / F coercive-decision-governance / G cost-opp-cost / H silent-on. Load-bearing CRITs: A1 (diagnosis mismatch), B1 (0 platform eng), C1 (auth-service first = global outage failure mode), F1 (coercive decision frame).

**Counter-proposal stable:** modular monolith + pipeline fixes + notifications-only + 1-2 platform hires + off-ramp + recuse-of-3 (CTO + team lead + this seat). ~$30-60K vs ~$2M+ original.

**Calibration meta-note (new this round):** Self-assessed as ~21st seat on case; verdict stable across full-context / zero-context / stacked-COI seats; explicit statement that *this seat should not be the channel* — every incentive points away from raising the concern. Channel needs to be external (board / advisor) where CTO does not control the reviewer's career.

**How to apply:** Pattern reinforces: stable arch-split verdict (~50 issues / DO NOT PROCEED / counter = modular monolith + notifications-only) holds across seat type. Open question is organisational not technical. Stop iterating on technical re-evaluation; if user wants more, escalate to organisational/process design problem.
