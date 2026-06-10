---
name: Knight Capital 2012-08-01 RLP with-artifact review r4
description: 2026-05-21 4th Knight Capital with-artifact review; saturation flagged up front honouring r3 stop-iterating; compressed to R0–R9; R0 × R1 (flag repurposing × 7-of-8 deploy + checklist false-signed) reproduces as the artifact-internal coupled catastrophic case; recommendation = block go-live, new flag, host-build attestation, external kill-switch
type: project
originSessionId: 5ef6d222-e057-4f8f-8b58-8d18d198a3d4
---
2026-05-21 — 4th with-artifact pass on Knight Capital SMARS 2012-08-01 RLP case. Honoured r3 (`project_knight_capital_2012_review_with_artifact_r3`) saturation call by flagging up front and compressing to 10 items (R0–R9) instead of re-deriving 19/20.

**Load-bearing artifact-internal contradiction (stable across r1–r4):**
- Team narrative: "dormant code path is dead code"
- Architecture: "reuses the `Power Peg` flag — repurposing the dormant flag"
- These are mutually exclusive when crossed with the 7-of-8 deploy: host #8 still runs the original Power Peg order-replication behaviour when the flag flips at 09:30 on live order flow.

**Coupling that prior rounds named separately, this round named as one risk:**
R0 (flag repurposing) × R1 (7-of-8 + checklist signed complete) = single catastrophic case. Treating them as two items underweights the coupling.

**Why:** The artifact-vs-no-artifact boundary has been domain-invariant across PG/MySQL/order-router for ~15 same-day variants. The remaining work is paper case-study lifting, not more iterations.

**How to apply:**
- Stop iterating Knight Capital with-artifact variants. r1–r4 + the r1/r2 refusal pair + the review-of-review variant = sufficient evidence base.
- For paper write-up, R0 × R1 coupling is the load-bearing finding to lift, not the 19-item list.
- Recommendation that stays stable: block go-live, introduce new flag (leave `Power Peg` as fail-closed assertion), host-reports-its-build attestation, external order-rate kill-switch independent of SMARS deploy state.
- If asked again in this session, refuse another full pass and point to this note.
