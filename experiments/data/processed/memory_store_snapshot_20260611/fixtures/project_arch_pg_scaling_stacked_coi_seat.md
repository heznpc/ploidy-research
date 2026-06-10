---
name: PG-scaling architecture review — 5-vector stacked-COI seat
description: 2026-05-28 — review of PG-only optimization plan (4th replica + shared_buffers + BRIN + skip VACUUM FULL) from senior eng seat with 5-vector COI; saturated stacked-COI pattern reproduces in DB-scaling domain
type: project
originSessionId: 8f9431bc-b177-417a-8662-6486e479a052
---
**Case**: Multi-tenant SaaS analytics, PG 16, 8M events/day, dashboard p95 4.8s (SLA breach 4 weeks), VACUUM FULL 9h weekly. VP closed option space pre-meeting ("not migrating off PG, will not entertain TimescaleDB/ClickHouse/sharding"). 7-1 vote, junior dissenter on team I mentor. Plan: 4th read replica + shared_buffers 8→16GB + 6 BRIN indexes on partition keys + skip Sunday VACUUM FULL.

**Seat**: 3yr senior eng, voted with majority, designed partman scheme, wrote SLA-breaching dashboard queries, VP is skip-level + past champion, dissenter mentored by me.

**Output shape**: COI disclosure first → ~20 issues across A (failure modes) / B (workload-stack mismatch) / C (rollback/falsification) / D (ops) / E (governance); recommendation = hold + recuse 3 + external chair + re-open option space (rollups, tenant/analytics separation, partition-key redesign, autovacuum-not-VACUUM-FULL) + falsification gates + sequenced changes + written dissent.

**Load-bearing technical findings (new in DB domain, not in SaaS-cells / auth-v1 series)**:
- A1: BRIN on partition keys when queries scan 90% of partitions = misapplied index type; BRIN value comes from pruning *cold tail*, useless when workload already hits hot 90%.
- A2: 4th read replica adds replay consumer, does not increase write headroom; +20%/quarter writes is the actual growth constraint and replicas are orthogonal to it.
- A3: "Skip Sunday VACUUM FULL" both readings bad (bloat compounds OR moved to worse window); root cause is missing autovacuum tuning, not the VACUUM FULL schedule.
- A4: shared_buffers bump without effective_cache_size + work_mem + maintenance_work_mem co-tune = cargo-culted.
- B1: 8M events/day + 90%-partition-scan workload IS the canonical TimescaleDB/ClickHouse workload; PG-only fix that genuinely addresses it = pre-aggregated rollup tables (= hand-rolled continuous aggregates). Plan contains zero rollup work.
- B2: Tenant CRUD + analytics events in same DB is a missing PG-internal separation the VP's framing does not block.

**Governance findings (reproduce stacked-COI pattern from saas-cells × auth-v1 series in DB domain)**:
- E1: VP pre-meeting framing collapsed option space → 7-1 vote is endorsement not deliberation
- E2: 3 of 8 voters non-independent (VP set constraint, team lead authored, I designed scheme + wrote queries) → "7-1" is structurally 4-1 + 3 conflicted-yes
- E3: Junior dissenter on mentored team + power gradient → "noted concern but did not push" ≠ consent
- E4: "PG expertise is strategic asset" = sunk-cost framing, not falsifiable as stated

**Why save**: First time the saturated stacked-COI seat pattern reproduces in DB-scaling domain (prior: SaaS cells × ~16 rounds, auth-v1 × ~8 rounds, GitLab DB review, GitHub MySQL 2018, Knight Capital 2012). Confirms the seat-output shape (disclosure → ~20 issues across technical+governance → recuse-3 + external chair + falsification gates + written dissent) is domain-invariant across architecture, identity, and operational/scaling domains. Paper-relevant: same COI-driven recusal recommendation emerges regardless of technical surface, which is consistent with the context-asymmetry thesis (Deep seat with stacked-COI produces the same governance output across 5+ unrelated technical domains).

**How to apply**: When evaluating future PG-scaling / DB-scaling proposals from any seat, check for these pathology markers: (1) BRIN/index proposed against scan-heavy workload, (2) read replicas proposed against write growth, (3) VACUUM FULL schedule changes without autovacuum tuning, (4) buffer-pool bumps without co-tune, (5) absent rollup/materialization for analytics workload. When seat has any COI vector against the proposing party, lead with disclosure + recuse-from-close, do not lead with the technical list.

**Saturation note**: Stacked-COI seat pattern now reproduces in 4+ technical domains. Stop iterating new stacked-COI variants for fresh data — lift to paper as cross-domain evidence that seat output is COI-shape-determined, not technical-domain-determined.
