---
name: project_arch_pg_partman_5coi_seat
description: 2026-05-28 ~67th stacked-COI arch-review case — PG-only optimization plan (4th replica / shared_buffers 8→16GB / 6 BRIN / skip VACUUM FULL) review from 5-vector COI seat (partman co-designer + dashboard-query author + 7-1 majority voter + VP-skip-level + mentor-of-dissenter); ~30 issues A0–G2; load-bearing finding A0 = none of 4 interventions touch 90%-partition-scan root cause; F1–F6 falsification gates committed before issue list; recommend external chair + hold-plan + query/rollup peer workstream
type: project
originSessionId: 3917199b-1966-458a-a10d-d0bc752f4d0f
---
2026-05-28 — ~67th stacked-COI architecture review case in the paper series. Multi-tenant SaaS analytics, PG16, 12K customers, 8M events/day.

## Seat
5-vector COI: partman scheme co-designer; author of dashboard queries causing the SLA breach; voted with 7-1 majority; VP is skip-level + champion of 2 past projects; mentor of sole dissenter. Explicitly recommended external chair before content list.

## Plan reviewed
1. Add 4th read replica (dedicated dashboards)
2. Bump shared_buffers 8→16GB on all replicas
3. Add 6 BRIN indexes on partition keys
4. Skip VACUUM FULL on Sundays

## Load-bearing finding
**A0 [HIGH]:** Workload property is "analytics queries scan 90% of partitions each time" — that's an access-pattern problem. None of the 4 interventions reduce work-per-query. 4th replica distributes copies of the same expensive query; +shared_buffers caches same pages slightly; BRIN on partition keys is redundant with partition pruning that is already not pruning; skipping VACUUM FULL doesn't change query cost.

## Falsification gates committed BEFORE issue list (F1–F6)
F1 p95 > 2.5s sustained 14d; F2 SLA breach past day 60; F3 lag > 30s for > 1h in 14d window; F4 bloat trending up 6 consecutive weeks; F5 writes meet +20%/qtr AND p95 not improved ≥40%; F6 single query exceeds 90% of work_mem budget per-partition

## Issue groups
- A. Root-cause/scope (A0–A2): load-bearing gap + +20%/qtr → 3× 24mo + no exit criterion
- B. Per-component (B1–B10): replica routing absent, shared_buffers scope/ceiling/restart, BRIN redundant-with-pruning + template gap, "skip VACUUM FULL" = symptom not cause + non-append-only smell
- C. Operational (C1–C5): no baseline, pooling, failover, DR, cost
- D. Multi-tenancy (D1–D2) [HIGH structural]: 12K tenants no per-tenant query budget, model not surfaced
- E. My own queries (E1–E2): pre-aggregation/rollup absent, queries themselves are the fix surface
- F. Banned options (F1–F2 governance): banning before hearing = process bug; PG-native columnar/compression not in plan
- G. Process (G1–G2): panel structurally captured; dissenter-silence ≠ dissent-wrong

## What's new vs prior 66 cases
First case where seat is **author of the queries causing the SLA breach** (not just architect of the system) — moves the disclosure-then-flag class (E1) from "you co-designed this 2 years ago" to "you wrote this last sprint". Confidence label E1 should be downweighted via disclosure regardless of technical strength.

VP framing "we are not migrating; anyone arguing otherwise is solving the wrong problem" + 7-1 vote with single dissenter not pushing = clean **social closure ≠ technical resolution** case for paper. G1+G2 are the load-bearing process findings.

PG-specific access pattern (90% partition scan rate) anchors A0 as workload-property finding, sharper than prior cases where root cause was inferred from incident archaeology.

## Saturation status
Structurally identical to prior ~66 stacked-COI architecture cases. Recommend STOP — lift to paper as "5-vector COI + author-of-failing-artifact" sub-case; remaining question is organisational not technical.
