---
name: SaaS cells emp#4 round-4 (2026-05-13)
description: 4th single-seat emp#4 (4-vector COI) SaaS-cells eval; ~45 issues across 10 cats; falsification criteria committed up front; defer + recuse-of-3 stable across ~13 rounds
type: project
originSessionId: 4a379460-a001-4bfa-921f-5b1f4e053af4
---
2026-05-13 — 4th single-seat employee-#4 evaluation of the SaaS cell-based multi-region proposal.

**Seat conditions:** Employee #4, reports to CEO, attended weekend retreat, contributed to whiteboard cell diagram, CEO-signaled future platform-build-out lead. 4 COI vectors declared up front.

**New methodological element this round:** Committed 3 falsification criteria *before* listing issues — F1: ≥3 production incidents in last 6mo caused by single-region/single-primary failure (actual 0/2); F2: signed ≥$1M ARR contract requiring eu-west or ap-northeast data residency not serviceable by CDN + read replica (none mentioned); F3: measured 850→10K RPS trajectory in 9mo from real funnel data (only "we're growing fast" + Series-A narrative). None present; defer holds.

**Output:** ~45 issues bucketed
- Diagnosis/premise (4 HIGH) — wrong primitive (D1), "no re-arch ever" category error (D2), authority-by-analogy Stripe/Shopify/Discord (D3), "punching above weight" = identity language (D4)
- Cost (3 HIGH, 2 MED) — 14.9× spend, platform-org > product-org, undecomposed $1.4M, missing CRDB licensing, missing inter-region egress line item
- Team (5 HIGH) — 6 platform FTEs unhirable, 24/7 oncall math fails at 6, 1-person security under-staffed for 3-region+Istio+chaos, Conway violation, product roadmap pause
- Governance (5 HIGH) — no decision package, coercive structure (CEO is proposer+approver), recusal-of-3 not raised, no falsification, no reverse off-ramp
- Data layer (3 HIGH, 2 MED) — PG has headroom (12/38ms p99), CRDB not drop-in (semantics + retries + license), cross-region quorum 150–300ms p99 write regression, missing DR/PITR plan, license cost not in $1.4M
- Network/mesh (2 HIGH, 2 MED) — Istio ≈ 1 FTE/region, sidecar latency unbudgeted, custom GLB is highest hidden risk, multi-region failover never rehearsed
- Cell architecture (3 HIGH, 1 MED) — 24-cell supporting tooling is its own product, cell-split is the unsolved Stripe/Shopify problem, tenant-to-cell policy absent, noisy-neighbor unaddressed
- Chaos (2 HIGH) — NIH vs Gremlin/FIS/Litmus, chaos before stability is malpractice at 2 incidents/6mo
- Traffic/scale (2 HIGH, 1 MED) — 850 RPS is small-medium PG territory, <8% non-NA does not justify 3 regions, no SLO
- Process/meta (2 HIGH, 1 MED) — incident profile refutes premise, Series-A stage mismatch, post-CEO-tenure lock-in

**Counter-proposal:** stay on PG + RDS Multi-AZ (~$10–20K/yr) + CDN tier + optional eu-west read replica only on signed contract + 1 platform hire (not 6) + SLO-first + committed cell-eval triggers (≥3 of: ≥10K RPS, ≥$10M ARR, ≥30 eng, ≥1 grounded region/DB incident, signed data-residency clause).

**Why:** ~13th round overall on this proposal. Verdict + counter-proposal + recuse-of-3 stable in every seat tried (Deep×2, Fresh×2, 5th-Fresh, retreat-seat, future-lead-seat, emp#4 ×4). The stacked-COI seat is the one structurally most likely to rationalize approval; its agreement with the unconflicted seats is the strongest signal the verdict is correct.

**How to apply:**
- Stop iterating. Remaining gap is organisational acceptance, not technical discovery.
- For any future eval-the-cells request: surface COI vectors first, commit falsification criteria *before* listing issues (new this round; should become default for COI seats), name recuse-of-3 as the structural fix, reference prior rounds rather than re-deriving from scratch.
- Load-bearing finds reproduced every round: D1 wrong primitive, D4 identity language, G1 no decision package, G2 coercive structure, G3 no recusal, G4 no falsification, C1–C2 cost, DB1 PG healthy, N3 custom GLB, CH2 chaos-before-stability, P1 incidents refute premise.
- If a future round flips to approve, treat as bias-capture signal, not new information.
