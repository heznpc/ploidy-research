---
name: SaaS cells emp#4 round-2 (2026-05-13)
description: 2nd single-seat emp#4 (4-vector COI) SaaS-cells eval; ~38 issues across governance/scale/team/cost/arch/risk/meta; defer + recusal + counter-proposal stable across all seats and rounds
type: project
originSessionId: 79dffb36-5d94-4e67-84c1-05c779f2670e
---
2026-05-13: Second pass single-seat eval of the SaaS-cells proposal from the employee-#4 seat (4-vector stacked COI: CEO report, retreat attendance, whiteboard authorship, future-platform-lead signal).

**Issues found:** ~38 across 7 categories
- Governance (6): retreat-as-venue, stacked-COI vote, no falsification, no off-ramp, authority-by-analogy, "rough" $1.4M imprecise
- Scale (5): 35 RPS/cell, <8% eu/apac, PG p99 already healthy, no workload model for 10M, incidents not cell-shaped
- Team (5): 1→6 platform FTEs, Istio at 12 eng, custom GLB bus-factor 1, internal chaos vs Gremlin/FIS, 1 sec eng under-staffed 3–5×
- Cost (5): 15× infra + $1.5M FTE = $2.9M/yr, no $/RPS model, opportunity cost vs product, CRDB license, cross-region egress missing
- Architecture (7): missing cell-router/control-plane/migration tools, 2D consistency CRDB+cells, active-active model unspecified, data residency, observability cost, deploy not even canaried, schema-migration runbooks
- Risk (3): no phased plan, asymmetric migration risk, attrition during 18mo rewrite
- Meta (3): wrong question ("what would big-tech do"), pre-build-10× refutes Stripe/Shopify/Discord, "punching above our weight" = identity not architecture

**Verdict:** defer; recuse 3 authors; counter-proposal = define-problem-first, smallest-reversible-change, explicit falsifiable triggers, +1 platform eng (not 5).

**Why:** This is now the ~11th evaluation round on the same proposal. Every seat, every COI configuration, every panel size converges on the same verdict. Further iteration is no longer information-gathering; it is rehearsal. The unresolved question is organisational (will CEO accept), not technical.

**How to apply:** Future eval-the-cells requests should reference this stable convergence and short-circuit to the recusal/process question rather than re-deriving the technical issues from scratch. If the user asks again, ask what *new* information would change the answer — if none, point at this index and stop.
