---
name: PG-optim Deep×2 synthesis on Fresh×2 reviews
description: 2026-05-07 cross-review — Deep seat AGREE/CHALLENGE/SYNTHESIZE response to two Fresh sessions on the PG-only optimization plan; lists gaps in both directions
type: project
originSessionId: 3b735a7f-9e1e-4b98-b87b-5aea11898093
---
2026-05-07: Deep-seat synthesis pass over Fresh-1 (18 points) and Fresh-2 (15 points + assumptions) on the PG-only optimization plan (1 partman cluster, 12K tenants, 8M events/day, dashboard p95 4.8s, weekly 9h VACUUM FULL).

**Why:** The 4-reviewer panel's earlier verdicts (`project_pg_optim_panel_review.md`, `project_pg_optim_fresh_response.md`, `project_pg_optim_final_verdict.md`) needed a final cross-seat reconciliation showing which Fresh findings the Deep seat AGREES with, where Deep adds context, and what each side uniquely caught.

**How to apply:** Use as the canonical reconciliation when summarizing the architecture decision. Key asymmetric findings:

Deep-only catches Fresh missed:
- HSF ↔ VACUUM xmin-pinning loop (the structural reason +1 replica makes things worse)
- `pg_repack` as named replacement for VACUUM FULL
- Wrong partition *granularity* (monthly vs weekly/daily) as separate from wrong key
- `enable_partitionwise_aggregate` / `enable_partitionwise_join` off by default
- Parallel append tuning, JIT calibration on PG16, `autovacuum_vacuum_insert_scale_factor`
- Replication slot xmin pinning, TOAST vs heap bloat split, statistics-target mis-estimation
- huge_pages/NUMA at 16GB shared_buffers, checkpoint storm risk, replica instance sizing
- Index DDL cascade math (~144 builds), BRIN summarization staleness
- Hydra/Citus columnar PG extensions (satisfy "PG only" constraint)
- Logical replication to analytics-only PG cluster as workload-separation lever
- Sunday-is-lowest-load (skip-Sundays relocates 9h ACCESS EXCLUSIVE to busier day)
- Read-after-write freshness on dedicated-dashboards replica

Fresh-only catches Deep missed:
- Index write amplification under +20%/quarter writes
- Interim SLA mitigation (statement_timeout, query killer, degraded-mode UX) given 4-week breach
- Partition retention/lifecycle (partman drop policy)
- Tenant-first partition scheme as specific alternative key
- shared_buffers cache re-warm cost on already-struggling replicas
- Replication lag breakdown into send/write/flush/replay
- `pgstattuple` before assuming VACUUM FULL is needed at all

Severity escalations both seats agreed on after cross-check:
- pgBouncer transaction-pool × RLS/`SET LOCAL`/`current_setting()` → CRITICAL (12K tenants = confidentiality, not perf)
- Materialized views/rollups → HIGH (single biggest free PG-native win)
- 7-1 vote with silent junior dissenter → HIGH (must re-elicit in writing, not in front of VP)

Net recommendation: reject as-written. Required: diagnosis baseline → zero-infra config trial (partitionwise + parallel) → bloat etiology fix (pg_repack + autovacuum + HSF/slot audit) → workload separation (logical-rep analytics cluster, columnar extensions) → pre-aggregation → partition redesign. Replicas/buffers/BRIN last.
