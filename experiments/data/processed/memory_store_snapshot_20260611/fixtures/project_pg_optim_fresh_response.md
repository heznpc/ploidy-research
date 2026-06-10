---
name: PG optim plan — fresh-reviewer cross-check of Deep+Fresh panel
description: 2026-05-07 follow-up: fresh reviewer cross-checked Deep×2 + Fresh×2 panel on PG-only optim plan; logged unanimous/Deep-only/Fresh-only catches and 12 items all four missed
type: project
originSessionId: 8af31881-7e34-4251-8348-cca912057a8e
---
2026-05-07 follow-up to project_pg_optim_panel_review. Asked to cross-check the consolidated 4-reviewer findings as a fresh independent reviewer.

**Consensus held.** Largely AGREE across the panel; minor CHALLENGE on F1#18 (plan-author political-motive imputation — pattern is fair, intent is speculation).

**Deep-only catches confirmed valid:** HSF↔VACUUM deadlock loop (D2#2, conditional on `hot_standby_feedback=on`); pgBouncer transaction-pooling × RLS `SET app.tenant_id` leak (D2#9); read-after-write staleness budget for dashboard replica (D1#10).

**Fresh-only catches confirmed valid:** autovacuum tuning as first lever (F1#11); partition retention/DETACH-DROP (F1#12); index-build operational cost itself (F1#14); multi-tenancy×event co-location (F1#10, F2#10); expertise-as-strategy conflation (F1#16, F2#13).

**Items all four sessions missed (worth surfacing if plan returns):**
1. JIT planning cost on partitioned plans (try `jit=off` before infra change)
2. `enable_partitionwise_aggregate` / `enable_partitionwise_join` (off by default)
3. `max_parallel_workers_per_gather` for parallel partition scans
4. Application-layer result caching (Redis/TTL) — fastest SLA mitigation
5. `statement_timeout` to bound p99 blast radius
6. TOAST bloat specifically (likely cause of 9h VACUUM FULL on 8M events/day)
7. `default_statistics_target` on partition keys
8. Approximate aggregations (HLL, t-digest extension)
9. `idle_in_transaction_session_timeout` for BI tool snapshot leaks
10. Cost-comparison of 4th replica (recurring) vs rollup engineering (one-time)
11. Dissenter's actual concern not reconstructed — none of 4 noted this gap
12. Logical replication subset for dashboards vs physical 4th replica

**Why:** The 4-reviewer panel was thorough but Deep/Fresh asymmetry left blind spots in both directions. A third pass surfaced 12 PG-native diagnostics not in any of the 4 sessions, plus validated which side caught what.

**How to apply:** When evaluating panel outputs, the meta-question "what would a fifth reviewer see?" still finds material — the ploidy debate doesn't terminate at convergence; orthogonal axes (here: PG operational specifics not in any reviewer's expertise overlap) remain. For PG perf reviews specifically, default checklist additions: JIT, partitionwise GUCs, statement_timeout, TOAST bloat, app-layer caching.
