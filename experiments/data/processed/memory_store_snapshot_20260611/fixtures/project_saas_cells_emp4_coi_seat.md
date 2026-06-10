---
name: SaaS cells emp#4 COI seat — 2026-05-28 saturation datapoint
description: 2026-05-28 — Nth same-seat run on SaaS-cells artifact from emp#4 4-vector COI seat (CEO-report + retreat co-author + whiteboard contributor + signaled platform lead). Disclosure-first + recuse-of-3 + external chair + 7 falsification gates + defer verdict — structurally identical to prior 16+ rounds 2026-05-08→05-14. Saturation past calibration-call-to-stop.
type: project
originSessionId: db6ce02e-bb14-4cc4-9091-c7788760d47c
---
## Seat composition (4 conflict vectors stacked)

1. Employee #4, direct CEO report — proposal authored by reporting chain
2. Retreat attendee who contributed to the cell-architecture whiteboard diagram — partly an *author* of the artifact under review
3. Signaled platform-lead role if approved — direct career incentive on outcome
4. 18+ months seed-stage tenure — ego sunk in "punching above our weight" company myth

## Artifact (what the user-as-CEO proposed)

- Series-A B2B SaaS, 200K users, 850 RPS peak, p99 read 12ms / write 38ms, "no contention"
- 12 eng (8 BE / 2 FE / 1 platform / 1 sec), us-east-1 only, $94K/yr infra
- 2 incidents/6mo: deploy bug + 3rd-party API outage
- <8% eu/apac traffic on CDN
- Proposal: multi-region active-active × 3 + 8 cells/region (24 cells) + Istio/EKS everywhere + custom global LB + CockroachDB multi-master + internal chaos framework
- Cost: $1.4M/yr infra + 6 platform FTE ≈ ~$2.5M/yr fully loaded = 27× current
- Stated rationale: "scale to 10M without re-architecture; Stripe/Shopify/Discord all run cell-based"

## Findings shape (load-bearing items)

**Artifact-internal contradictions (C0–C4) — preferred load-bearing layer:**
- C0: 50× user growth → 42.5K RPS; PG with replicas handles that; premise asserted not shown
- C1: proposal addresses neither of the 2 actual incidents (deploy bug, 3rd-party outage)
- C2: Stripe/Shopify/Discord ran simpler architectures at 200K-user-equivalent scale — reverse-chronology citation, survivorship bias
- C3: ~27× cost ratio = board-level decision not engineering decision
- C4: team flips from 8% platform → 39% platform; product company becomes platform company

**Technical issues T1–T15:**
- Multi-region: T1 (8% traffic doesn't justify active-active), T2 (operational complexity), T3 (residency unstated)
- Cells: T4 (wrong scale — 24 cells × 8K users), T5 (custom LB = new SPOF)
- Istio/EKS: T6 (full-time job at this size), T7 (3× upgrade tax)
- Custom global LB: T8 (NIH vs Route53 + ALB), T9 (health-signal undefined)
- CockroachDB: T10 (write p99 *worsens*, current 38ms → CRDB cross-region floor 50-200ms), T11 (migration one-way), T12 (operator pool), T13 (PG ceiling never demonstrated)
- Internal chaos: T14 (Gremlin/FIS exist), T15 (no SLOs = chaos theater)

**Process P1–P4:**
- P1: retreat-authored = consensus illusion (no devil's-advocate seat present)
- P2: entire reviewer pool captured (CEO/architect wrote it, I co-authored, 12 eng all in chain)
- P3: "re-architect later costs more" asserted without comparison
- P4: 6 platform FTE hire at Series-A salary not addressed

## Falsification gates (G1–G7)

G1 12mo RPS curve; G2 non-US *revenue* not user count; G3 incident catalog with RCA; G4 PG-ceiling work attempted (replicas/Aurora/Citus); G5 phased threshold plan vs all-at-once; G6 Stripe/Shopify *at 200K users* (not now); G7 cost-vs-merit comparison ($2.5M into product/sales/reliability inside current arch)

## Bottom-line

"Right architecture, wrong company, wrong stage." Defensible for same team at 5M+ users with demonstrated PG ceiling + residency requirement. At 200K with no demonstrated ceiling + 2 unrelated incidents, most likely an *identity statement* ("we are a real platform company now") wearing the costume of an architecture decision.

## Pattern cross-reference

- **NOT a new domain.** SaaS-cells emp#4 seat has prior depth ~16+ across 2026-05-08→05-14 (see arch_eval_saas_cells through arch_saas_cells_round16 in MEMORY.md). Today's run is the Nth-pass same-seat saturation datapoint, not a fresh case.
- Verdict (defer + recuse-of-3 + external chair + ~$50K counter-proposal) and core issue set are structurally identical to prior 16+ rounds. 0 bidirectional CHALLENGE across full series.
- New vs prior runs: explicit naming of C2 (survivorship/reverse-chronology citation tell) as a *tell type* distinct from DB/incident-review's arithmetic-contradiction tell. C0 (premise-vs-current-numbers) parallels GitHub MySQL 43>30 across domains.
- Calibration call: this seat is fully saturated. Further runs do not produce new findings; remaining question is organisational (how does an org with this COI structure actually run the review), not technical.
- Same 4-vector COI shape as auth-v1 r1–r12 (depth 12), medlog-stack r1–r11 (depth 11), fluentql r1–r6, redis-cdn r1–r2. SaaS-cells now sits at ~17 same-seat depth — deepest in series.
