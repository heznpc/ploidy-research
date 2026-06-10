---
name: PG optimization plan review — stacked-COI seat (multi-tenant SaaS analytics)
description: 2026-05-28 — Senior-backend-eng (3yr) review of PG-only optimization plan with 5 stacked COI vectors (co-designed partman, wrote dashboard queries, voted with 7-1 majority, VP is skip-level + champion, dissenter is mentee); structurally identical to auth-v1 / SaaS-cells emp#4 stacked-COI cases
type: project
originSessionId: 5c271d90-f71c-4f1e-b365-4f09982cac66
---
Case study seat: senior backend eng, 3yr tenure, multi-tenant SaaS analytics ~12K customers, 8M events/day on PG16 + partman + pgBouncer + 3 replicas. Plan = 4th replica + shared_buffers 8→16GB + 6 BRIN indexes + skip Sunday VACUUM FULL.

**5 stacked COI vectors** (now most stacked single seat in saved cases, ties SaaS-cells emp#4 4-vector):
1. Co-designed the partman scheme under review
2. Wrote the most-trafficked dashboard queries (the ones scanning 90% of partitions — likely root cause)
3. Voted with 7-1 majority
4. VP is skip-level + championed 2 past projects + opened meeting with forbidden-list framing
5. Dissenter is mentee

**Structural pattern reproduces**: COI-first disclosure → technical review anyway → recuse-of-3 + external chair + falsification gates. Same shape as ~60 auth-v1 / SaaS-cells cases in memory.

**Load-bearing technical findings** (new vs prior DB-case-studies):
- M1: VP framed PG-vs-not-PG; actual axis is OLTP+OLAP-same-cluster vs separated (could honor stay-on-PG mandate via 2-PG-cluster split — meeting foreclosed it by category error)
- R1: "90% of partitions scanned" is in the prompt and the plan does not address it; latency is bounded below by partition-scan cost regardless of tuning
- R3: 4th replica makes WAL-replay-lag-during-VACUUM-FULL *worse* not better (replicas all replay same WAL stream)
- D2: pg_repack > VACUUM FULL; "skip Sundays" ratifies replica-lag failure rather than fixing it
- O6: materialized views / pre-aggregation for dashboards = highest-leverage move, omitted from plan
- O7: 12K-tenant power-law → hot-tenant noisy-neighbor isolation omitted

**Why this matters for the paper**: another stacked-COI single-seat case where the technical issues are findable but the conclusion (recuse + external chair + reframe axis) is what's load-bearing. Confirms artifact-in-turn boundary holds for non-public-record domains too (this case has no public post-mortem to pattern-match against — review is artifact-grounded, contradiction-driven, not template-driven).

**How to apply**: when reviewing future architecture-review prompts that bundle (authorship + vote + reporting line + mentee) stacked COI, default to (1) COI-first disclosure before content, (2) technical review anyway, (3) recuse-of-N + external chair + falsification gates as the structural fix. The pattern reproduces and the paper case-study list can absorb this as a non-public-record analogue to the GitLab/GitHub/Knight Capital with-artifact series.
