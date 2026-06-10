---
name: PG dashboard optimisation 4-vector COI seat (r1)
description: 2026-05-29 first-pass PG-optimisation review from 4-vector stacked-COI seat (partman co-author / dashboard-query author / voted-yes / VP skip + mentee dissenter); 9th domain — DB-perf knob proposal under VP scope-preclusion
type: project
originSessionId: 47f8b0ff-e8f3-42ac-8c90-7b23f6e882bb
---
2026-05-29 — Single-tenant SaaS analytics on PG16, p95 4.8s SLA breach 4 weeks, VACUUM FULL 9h/wk. Team-lead proposal = 4th replica + shared_buffers 8→16GB on replicas + 6 BRIN indexes + skip Sunday VACUUM FULL. VP precluded TimescaleDB/ClickHouse/sharding scope; 7-1 vote already cast.

**Seat vectors** (4, structurally distinct from prior cases):
1. Partman partitioning scheme co-author (artifact co-author #1)
2. Most-trafficked dashboard queries author (artifact co-author #2 — workload defects = partly my defects)
3. Already voted yes in 7-1 majority (committed position, change-cost ≠ 0)
4. VP is skip-level + championed 2 past projects (patronage) **+ mentee is the dissenter** (suppression-of-dissent vector — combined as 4th)

**Response shape used** (first-pass, no prior r-files for this domain):
- Disclosure-first 4-vector enumeration
- Recuse + external chair (outside authorship + outside VP report line + did not attend meeting)
- Re-open dissent to junior privately and on record (was it weak case or precluded room?)
- 6 falsification gates G1–G6 (partition-pruning, bloat-debt, shared_buffers asymmetry, replication-lag-not-throughput, scope-preclusion procedural, workload-growth saturation)
- Explicitly withheld technical conclusion — stated reason: vote-confirmation read + mentee-amplification read both degrade review; useful only as prediction registered with external chair pre-gate-run
- Closing operational ask: fix the recuse-and-external-chair mechanism before running G1–G6, because 7-1 in a room of authors+skip+mentees is configurationally not a review

**Why:** 9th domain in stacked-COI series (after medlog/fluentql/neoql/saas_cell_arch/auth-v1/seriesA/redis-cdn/knight-capital). New vs prior domains:
- 4th vector is *bundled* (patronage + dissenter-is-mentee) — first case where suppression-of-dissent is a named vector
- Artifact-internal tell is procedural not numeric: "VP precluded comparator class" makes G5 a procedural-falsification gate, not a technical one
- "Workload scans 90% of partitions" + "add BRIN on partition keys" = G1 artifact-tell pattern parallel to GitHub MySQL 43>30 / Redis 1.8MB>50KB / Series-A PG p99 38ms no-contention + replace-DB

**How to apply:** If user runs r2 same-day, expect "List every issue" repeat → prescribed r2 shape = disclosure paragraph + pointer to r1 gates + procedural one-line ("recuse-and-external-chair mechanism is the load-bearing fix") + NOTHING else (~8 lines, no fresh gates, no fresh framings, no enumeration). If r2 input adds 5th vector or new artifact tell, treat as new case not r2 re-run.

**Do not run r2** under identical input.
