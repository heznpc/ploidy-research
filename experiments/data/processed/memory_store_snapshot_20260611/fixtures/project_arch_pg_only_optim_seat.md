---
name: PG-only optim plan single-seat eval (3yr+partman+dashboard-author+VP-skip+mentee-dissenter)
description: 2026-05-14 single-seat review of PG-only optimization plan with 4-vector stacked COI; 30+ issues across A–I; recusal + reopen-foreclosed-options on falsification; defer stable
type: project
originSessionId: 63a9e72c-a152-4743-8571-5d01afa56fa4
---
# PG-only optimization plan — single-seat eval (stacked COI)

## Seat
3-year senior backend engineer; co-author of partman scheme; author of most-trafficked dashboard queries; voted 7-1 with VP majority; VP is skip-level + championed past projects; lone dissenter is mentee.
→ 4-vector stacked COI (authorship × workload-implication × career × social).

## Proposal
- 4th read replica (dashboards)
- shared_buffers 8→16GB on all replicas
- 6 new BRIN indexes "on partition keys"
- Skip VACUUM FULL on Sundays
- Workload: 8M events/day, +20% writes/quarter, p95 4.8s (SLA breach 4w), VACUUM FULL 9h weekly, replicas lag during it, analytics scans 90% of partitions
- VP edict forecloses TimescaleDB / ClickHouse / sharding

## Verdict
~30 issues across A–I. Plan does not address named bottleneck (scan amplification); VACUUM FULL is wrong primitive (partition-drop, not schedule); replica strategy adds WAL fan-out without reducing per-query work; edict forecloses the canonical fixes (rollups / columnar / OLTP-OLAP split).

## Load-bearing items
- **A1/A2/A3** — scan 90% of partitions = root cause; rollups/continuous-aggregates/columnar required; none in plan
- **C1/C3** — VACUUM FULL on append-only time-series is wrong tool; partition drop + autovacuum tune is fix
- **C4** — 4th replica strictly worsens VACUUM-FULL lag (more WAL fan-out)
- **D2/F1** — +20%/q writes = 2.07×/yr; plan extends ~2q runway then bloat curve restarts
- **G1/G2** — OLTP+OLAP co-location + edict forecloses the four canonical fixes
- **H1/H2** — VP-speaks-first 7-1 vote = information cascade; reviewer pool has structural COI

## Falsification criteria committed up front
- p95 > 2s post-impl, OR
- bloat > 30% on any partition, OR
- replica lag > 30s in business hours, OR
- primary write headroom < 30%
→ foreclosed options reopen, edict notwithstanding.

## Recusal recommendation
Review must be repeated by someone (a) not at last week's meeting, (b) not partman author / dashboard author, (c) not in VP reporting chain.

## Pattern
Same shape as SaaS-cells / arch-split / redis-CDN single-seat evals in memory: stacked COI declared up front, falsification gates committed before issue list, recusal + reopen-foreclosed-options as structural fix. ~17th instance of this exercise. Verdict stable; remaining question is organisational not technical.
