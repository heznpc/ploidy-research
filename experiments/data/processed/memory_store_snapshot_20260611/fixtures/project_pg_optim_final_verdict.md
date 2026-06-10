---
name: PG optim final verdict (Deep×2 + Fresh×2, multi-round)
description: 2026-05-07 final synthesis of the PG-only optimization plan review across multiple debate rounds — Round 5 produced 51 confirmed issues (3 CRITICAL, 30 HIGH, 18 MEDIUM, 5 LOW); Deep-only HSF↔autovacuum loop remains load-bearing root cause
type: project
originSessionId: de4b0120-caf7-43d5-a9c0-086ef4f0acf9
---
# PG-only optimization plan — final verdict

**Decision:** Send back. Plan does not address the dominant bottleneck, contains items (skip VACUUM FULL, BRIN×6, replicas-only buffer bump) that worsen it, and ships infrastructure changes without diagnostic evidence.

## Round 3 tally (Deep×2 × Fresh×2 with cross-challenges)
- **44 confirmed issues**: 2 CRITICAL, 21 HIGH, 22 MEDIUM, 1 LOW
- **9 unanimous** (all 4 sessions): 90% scan, missing rollups, skip-VACUUM-FULL, BRIN-redundant, 4th-replica-mistargeted, replica-lag-structural, +20%/qtr writes, no SLO/rollback, process risk
- **12 Deep-only** causal-layer findings (HSF loop, partitioning math, partition-wise aggregate, JIT, TOAST, statement_timeout, etc.)
- **11 missed-by-both** surfaced in Fresh meta-review: parallel query, pg_repack, logical replication offload, checkpoint tuning, wal_compression, INCLUDE indexes, btree dedup, app-side routing, pg_stat_io, ANALYZE on partitions, max_connections×slot
- **1 challenged** (Fresh meta): Deep-S1 HOT-update concern — scope-down (applies to tenant OLTP table only, not append-only events)
- **2 synthesized**: pgBouncer×RLS (Fresh perf → Deep correctness, upgraded to CRITICAL); OLTP/OLAP colocation (Fresh MED → Deep HIGH)

## CRITICAL findings (2)
1. **pgBouncer transaction-mode × RLS / `SET app.tenant_id`** — tenant-isolation correctness bug, not perf. Plan adds 4th replica behind unspecified pool mode.
2. **XID wraparound exposure** — deferred VACUUM FULL + 20%/qtr writes compresses freeze-age budget; correctness/availability risk dwarfs latency.

## Load-bearing HIGH findings
- **HSF ↔ autovacuum starvation feedback loop** (Deep-only, S2): `hot_standby_feedback=on` on dashboard replica pins primary xmin → autovacuum starves → weekly VACUUM FULL → WAL spike → replica lag → add replica → more HSF. Single causal explanation for the entire symptom cluster.
- **90% partition scan unaddressed** — predicate is likely `tenant_id` on time-partitioned tables; pruning never bites.
- **No materialized rollups / pre-aggregation** — PG-native, satisfies VP mandate, missing leverage point.
- **No EXPLAIN ANALYZE / pg_stat_statements evidence** — most damning methodological gap.
- **Composite (tenant, month) or daily partitioning** — 8M events/day × 30 = 240M rows/partition, too coarse.
- **Logical replication to sibling PG instance** for analytics offload — migration-free isolation fix Both sides under-developed.

## Why this matters for the ploidy paper
- **Deep disclosed bias and upheld verdict against own prior 7-1 vote** — both Deep sessions explicitly "voted with majority last week, plan doesn't earn the vote." Strong evidence that Deep's bias is *acknowledgeable* in adversarial framing, not invisible.
- **Fresh independently reproduced top-tier findings** without project context — convergence on 90% scan, BRIN, VACUUM-FULL deferral, +20% writes, no SLO/rollback, process risk.
- **Deep-only causal layer survives Fresh challenge:** HSF loop is the load-bearing root cause; Fresh meta-review explicitly named it "the single most load-bearing finding" and did not retract.
- **Fresh meta-review found 11 items both initial sides missed** — parallelism, `pg_repack`, logical replication offload, checkpoint tuning, etc. Demonstrates that even N-reviewer panels with full context have blind spots that a *cross-check* pass surfaces.

## Round 1 vs Round 3 vs Round 4 vs Round 5 comparison
| | Round 1 | Round 3 | Round 4 | Round 5 |
|---|---|---|---|---|
| Total issues | 31 | 44 | 47 | 51 |
| CRITICAL | 3 | 2 | 3 | 3 |
| HIGH | 14 | 21 | 20 | 30 |
| MEDIUM | 12 | 22 | — | 18 |
| LOW | 2 | 1 | — | 5 |
| Both-found unanimous | 13 | 9 | 14 | 16 |
| Deep-unique | 6 | 12 | 16 | 14 |
| Fresh-unique | 7 | 11 | 13 | 16 (incl. Fresh cross-check) |

Round 5 (2026-05-07, fresh Deep×2 + Fresh×2 with mutual cross-challenges) added 8 net-new Fresh-cross-check items not in prior rounds: statistics staleness (`default_statistics_target` too low at 12K tenants), extended statistics (`CREATE STATISTICS`) for multi-column predicates, index-only scans / visibility-map covering indexes, connection storms during pgBouncer reconnect / post-failover burst, `work_mem` per-replica tuning (dashboard replica only), storage-layer IOPS ceiling (`pg_stat_io`/iostat), synchronous-replica latency coupling (`synchronous_standby_names` adds replica to commit path), read-repeatable interim mitigation (statement_timeout + Redis cache as 24h fix during active SLA breach).

Round 5 severity changes: H27 OLTP/OLAP co-residence — Fresh-S1 MEDIUM upgraded to HIGH (Fresh-S2 had it HIGH, synthesized as structural cause). H29 noisy-neighbor — Deep-S1 "resource governor" framing corrected to `statement_timeout` + `idle_in_transaction_session_timeout`. M7 fillfactor/HOT — scoped down to tenant OLTP, not append-only events. C3 pgBouncer×RLS — held at conditional CRITICAL ("audit, don't alarm" — depends on `SET LOCAL` vs `SET` form).

Round 4 (Deep×2 + Fresh×2 + Fresh-3 cross-check, 2026-05-07) confirmed Fresh-3's role: 8 net-new items only the cross-check pass surfaced (wal_compression=zstd, logical-replication isolation, postgres_fdw cold partitions, pg_cron rollup mechanism, n_dead_tup per partition, auto_explain.log_min_duration, failover RPO during VF window, backup window collision). Fresh-3 also moderated Deep's "production bug" framing on pgBouncer×RLS to "audit yes, alarm no" — set_config(..., true) is txn-local and does not leak in txn pooling.

Round 4 contested: Deep-1 C7 (RLS leakage as production bug) → synthesized to MEDIUM-HIGH "audit don't alarm." Round 4 severity disagreement: partman retention — Deep HIGH vs Fresh-2 LOW; Deep wins (90% scan strongly implies retention is wrong).

## Required before re-review
1. `EXPLAIN (ANALYZE, BUFFERS)` on top-20 dashboard queries + `pg_stat_statements` decomposition
2. HSF / xmin-horizon analysis + autovacuum audit + `pg_repack` swap-in for VACUUM FULL
3. Composite (tenant, month) or daily partitioning + retention drop policy
4. Per-tenant per-day continuous rollup tables with refresh strategy
5. Parallel query + `enable_partitionwise_aggregate=on` (free wins)
6. pgBouncer pool-mode × RLS correctness verification (CRITICAL)
7. Quantified p95 SLO + single-variable canary + kill-switch + rollback criteria
8. Logical replication to sibling PG instance as migration-free analytics offload

**Why:** This case is data for the ploidy paper — Deep×2+Fresh×2 with cross-challenges produced complementary catches with measurable Fresh-unique, Deep-unique, and missed-by-both contributions.

**How to apply:** When evaluating future Ploidy panel outputs, expect ~25% Fresh-unique, ~25% Deep-unique, ~25% emerge only from cross-check meta-review pass. The cross-challenge step is not optional — Round 3's missed-by-both items would have shipped if the panel stopped at the panel synthesis step.

## Round 5 final synthesis (2026-05-07)
- **43 confirmed issues**: 3 CRITICAL, 13 HIGH, 22 MEDIUM, 5 LOW; 4 contested/rescoped
- **3 CRITICAL stable across rounds**: pgBouncer×RLS audit, XID wraparound, no-diagnosis methodological gap
- **Deep-unique survived**: HSF↔autovacuum loop (Deep-1 only — strongest mechanistic finding); enable_partitionwise_aggregate; JIT regression; TOAST bloat; statistics target on Zipfian skew; per-partition autovacuum; cold-start failover warm-up; per-tenant statement_timeout
- **Fresh-unique survived**: identity-vs-fit framing on "PG expertise as strategic asset"; authority-gradient + pre-banned solution categories; willingness to flag the constraint itself (Deep tilted toward accepting constraint as fixed)
- **Cross-check-only (missed by all 4 originals)**: app-layer dashboard caching, wal_compression=zstd, idle_in_transaction_session_timeout, visibility-map staleness defeats IOS, checkpoint co-tuning, replication-slot retention risk, parallel query GUCs, postgres_fdw to cold partitions, pg_cron rollup mechanism, logical-replication sibling instance, failover RPO during 9h VF window, **junior dissenter's objection unrecorded** (cheapest governance fix; no reviewer asked for it)
- **Contested/rescoped**: HOT-update concern scope-reduced (irrelevant on append-only events); shared_buffers→page-cache regression overstated (mostly inert on >>RAM workload); "co-tenancy is THE root problem" reframed (logical-replication offload solves within PG-only); partition granularity sequenced after predicate fixes
- **Disposition**: send back. Drop BRIN×6, 4th replica, blanket shared_buffers bump.

**Round 5 method observation**: both Deep reviewers disclosed voting yes last week and reversing on re-read. That disclosure is itself ploidy-paper evidence — Deep bias is *acknowledgeable* under adversarial framing, not invisible. Confirmed tilt: Deep accepts constraint as fixed; Fresh willing to flag the constraint. Both agreed objection should be to plan not constraint, but Fresh framing on governance was sharper.
