---
name: PG optim 5th-reviewer cross-check (full panel)
description: 2026-05-07 — Fresh 5th-reviewer pass cross-checking the Fresh×2 + Deep×2 panel on PG-only optim plan; AGREE/CHALLENGE/SYNTHESIZE per point + 14 panel gaps
type: project
originSessionId: 63c62253-c5f1-4669-b9cc-894c51ca083f
---
5th-reviewer (zero-context Fresh) pass over the full 4-reviewer panel (Fresh×2 + Deep×2) on the PG-only optimization plan.

**Verdicts:** Mostly AGREE. Few SYNTHESIZE on degree (25%-RAM folklore, row-store overstatement, columnar extension risk, failover/PITR severity). No CHALLENGE — the panel's findings held up.

**Strongest panel insight:** Deep 2 B2 — HSF ↔ VACUUM ↔ replay loop. Reframes plan from "incremental tuning" to "self-defeating architecture." Fresh seats found diagnostic gaps; Deep seats found the structural feedback loop. Complementary, not redundant.

**Strongest gap missed by all 4 reviewers:** `work_mem`/sort-spill diagnosis. p95=4.8s on analytical SQL is more often `temp_files` activity than partition-scan volume.

**Other panel-wide gaps (14 total):**
1. work_mem / sort-spill / `log_temp_files`
2. `max_locks_per_transaction` × partman child locks
3. `statement_timeout` / `idle_in_transaction_session_timeout` (direct mitigation for long-txn blocking autovacuum)
4. `auto_explain` (should be first lever, before pg_stat_statements ranking)
5. `pg_buffercache` (measure working set vs guess shared_buffers)
6. `random_page_cost` / `effective_io_concurrency` (SSD defaults)
7. `enable_async_append` (PG14+)
8. Prepared-statement caching × pgBouncer txn-mode (tail latency)
9. Index bloat vs table bloat distinction (`REINDEX CONCURRENTLY` vs `pg_repack`)
10. `pgstattuple` / `pgstattuple_approx` (measure before repack)
11. CTE materialization keyword change PG12+ (silent plan regression on upgrade)
12. Logical-replication slot lag vs physical (if F5 adopted)
13. `temp_buffers` / `maintenance_work_mem` (index-build speed for D4's 144 builds)
14. Per-tenant resource isolation (pg_cgroups, GUC) at 12K tenants

**Promotions suggested:**
- Deep 2 F5 (logical-replicated analytics cluster) → HIGH
- Deep 1 #23 (failover/PITR impact) → MEDIUM
- Deep 2 D4 (144 cascading concurrent index builds) → HIGH operational risk

**Confidentiality, not just perf:** Deep 1 #7 / Deep 2 B3 — pgBouncer txn-mode + RLS/GUC tenant context across 12K tenants is a tenant-leak risk that should be CRITICAL.

**How to apply:** When this PG plan resurfaces, the panel synthesis is in this file + the four prior project_pg_optim_* memories. The 5th-reviewer pass concluded the panel was sound but incomplete on PG-internal levers (work_mem, lock count, auto_explain, pg_buffercache).
