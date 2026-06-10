---
name: arch saas cells final v6
description: 2026-05-13 round-6 final Deep×2+Fresh×2+bidirectional cross verdict on SaaS cell-architecture proposal — 61 issues (7 CRIT/32 HIGH/13 MED/1 DROP); 0 CHALLENGE bidirectional; defer stable across 6 rounds; load-bearing = unanchored premise + 1-platform-eng + proposer-as-approver + 3-COI + no-SLOs + 30× run-rate
type: project
originSessionId: 5e90e017-6f4f-4c07-966e-6f9ee09a417d
---
Round-6 verdict on SaaS cell-architecture proposal (12-eng Series-A, 200K users, 850 RPS, proposing 8 cells × 3 regions + Istio + CockroachDB + custom GLB + chaos framework, $94K → $1.4M + 6 FTEs).

**Result:** 61 issues (7 CRIT / 32 HIGH / 13 MED / 0 LOW / 1 DROP). 0 strict CHALLENGEs bidirectional. Defer recommendation stable across 6 rounds.

**Load-bearing chain (unanimous):**
- S1 unanchored 10M premise (CRIT)
- T1 1 platform eng cannot operate 24 cells (CRIT)
- P1 proposer = approver (CRIT)
- P3 3 conflicted authors require recusal (CRIT)
- P4 no SLOs = unfalsifiable (CRIT)
- C1 30× run-rate hit (CRIT)
- S7 no stated problem (CRIT)

**Deep-only catches (Fresh missed):** P3 recusal structural fix, P5 off-ramp, P8 future-lead pre-decision defect, P13 falsification criteria, P14 external advisor, P15 COI self-disclosure protocol, D2 CRDB schema-feature audit (advisory locks, LISTEN/NOTIFY, FK actions), D3 SSI semantics, D4 tenant locality, D7 GLB-flapping + in-flight writes, C2 CFO + burn model.

**Fresh-only catches (Deep under-weighted):** S8 cell-utilization math (24 cells × 35 RPS), D10 sidecar +1–5ms p99 regression, T10 6–12mo hiring timeline anchor, P9 Stripe-on-Mongo counter-anchor.

**Severity escalations adopted in cross-review:**
- F1-10 / F2-11 / D5 combinatorial failure modes → CRITICAL
- D11 migration risk itself → CRITICAL
- F2-8 cell-utilization arithmetic → HIGH (most decisive single number)
- T3 Istio tax → HIGH (mesh CVE/cert-rotation surface)
- T6 chaos framework → HIGH
- P2 weekend authorship → HIGH ($2.5M/yr no-RFC commitment)

**Dropped:** Fresh F2-20 frontend/backend ratio — CHALLENGED, doesn't bear on infra decision.

**Counter-proposal (stable 6 rounds):**
- Phase 0 (4–8 wk, ~$0): SLOs + cohort model + customer-pull evidence
- Phase 1 (1–2 qtr, ~$200–400K): PG read replica + CDN + Multi-AZ + deploy gates + k6
- Phase 2 (defer): re-evaluate at 5M users or >25% non-US revenue

**Process fix (must precede technical):** recuse CEO + architect + future-lead; external advisor cold review; written falsification criteria; unwind future-lead signal pre-decision.

**Why:** Same proposal evaluated from progressively stacked-COI seats (rounds 1–6); verdict and counter-proposal sharpened, not softened. Session evidence for paper: COI self-disclosure + recusal protocol produces stable verdicts under stacked COI, contradicting the prediction that context bias monotonically softens critique.

**How to apply:** This is one of the most heavily replicated debates in memory (6 rounds, ~250+ unique issues across versions). Pattern is robust enough to cite as the canonical "premature scale architecture" exemplar in the paper. Fresh-side systematic gap: under-grading consequence-chain items (severity floor), missing governance-structure fixes. Deep-side systematic gap: missing concrete arithmetic anchors (cell utilization, sidecar latency).
