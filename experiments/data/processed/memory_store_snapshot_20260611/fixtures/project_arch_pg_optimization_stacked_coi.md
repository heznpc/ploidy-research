---
name: project_arch_pg_optimization_stacked_coi
description: 2026-05-28 — stacked-COI architecture review of PostgreSQL optimization plan (4th replica + shared_buffers + BRIN + skip-VACUUM FULL); first non-SaaS-cells / non-auth-v1 case to reproduce the same 5-vector COI pattern; ~63rd stacked-COI case overall
type: project
originSessionId: 94d9d656-a6c1-44f9-85a6-86c678c95069
---
2026-05-28 — new domain (PG ops optimization for ~12K-tenant analytics SaaS) hit with the same stacked-COI seat shape that the SaaS-cells (~16 rounds) and auth-v1 (~8 rounds) cases reproduced in. Confirms the COI-structural finding is *domain-invariant* across cell architecture, auth migration, and DB optimization.

**Seat:** 3yr senior backend eng. Co-designed partman scheme (the substrate of the failure). Wrote dashboard queries (the queries scanning 90% partitions). Voted with 7-1 majority. VP is skip-level + champion of 2 past projects. Lone dissenter (junior) is on a team the seat-holder mentors. 5 conflict vectors stacked.

**Plan being reviewed:** 4th read replica, shared_buffers 8→16GB on replicas, 6 BRIN indexes on partition keys, skip VACUUM FULL on Sundays.

**Load-bearing technical finding:** plan does not address the diagnosis. 90%-partition-scan = partition pruning is broken (query/schema problem); weekly 9h VACUUM FULL = autovacuum / HOT / fillfactor / long-txn problem; replica-lag-during-refresh = WAL-emission / sync problem; writes +20%/quarter = growth-curve problem. None of the four plan items touch any of those four root causes. Capacity bump dressed as remediation; buys ~1 quarter of headroom and worsens the next decision's starting point.

**Per-item:**
- 4th replica: doesn't fix write-side bottleneck; isolating dashboards on one replica makes that replica the slow component; routing/staleness not specified.
- shared_buffers 8→16GB on replicas only: working-set math missing (likely 100s of GB events); primary untouched; effective_cache_size / work_mem unchanged so query plans don't change.
- 6 BRIN on partition keys: BRIN on the partition column itself is wrong shape; pruning already covers that axis; BRIN earns its keep on correlated *non-partition* columns; 90% partition scan = pruning is broken, no index fixes that.
- Skip VACUUM FULL on Sundays: doesn't reclaim bloat; weekly FULL itself is the finding (autovacuum / HOT / fillfactor / xmin-pinning under-diagnosed); right replacement is pg_repack + per-relation autovacuum re-tuning.

**Issues not named in the plan (HIGH confidence):** 90%-partition-scan as the headline, MV/pre-aggregation absent, mixed OLTP+OLAP on one cluster (the architectural issue the VP's framing forbids naming), no SLO / falsification gate, no growth-curve math (2.07× over 4 quarters), replication-lag-during-VACUUM unaddressed, no instrumentation-first step (`pg_stat_statements`, `pg_stat_user_tables`, `pg_stat_replication`, `pg_buffercache`), no off-ramp.

**VP framing red flag:** "I will not entertain TimescaleDB, ClickHouse, or sharding-as-rewrite" closes off the three standard remediations for this exact symptom set *before* diagnosis. Pre-rejected option space.

**7-1 vote is a category error:** skip-level VP + 6 senior peers + mentor-of-dissenter = power gradient that produces silence, not consensus. Treating the junior's non-pushing as agreement is structurally wrong.

**Recommended pattern (now stable across 3 domains — cells / auth / PG-ops):**
1. Recusal of the conflicted seat.
2. External reviewer with no equity / no reporting line to VP / no co-authorship on the failed component.
3. Dissenter's written objection circulated *without* commentary from the conflicted parties.
4. Falsification gates committed *before* the plan ships (p95 target, replication lag ceiling, partition-scan ratio target, cost ceiling vs. excluded alternatives, withdrawal condition).
5. Instrumentation before capacity.
6. One-page cost of *one* excluded alternative even if VP's framing stands.

**Why this case matters for the paper:**
- 3rd domain to reproduce the stacked-COI structural finding (cells = capacity/sharding; auth = security migration; PG-ops = DB tuning).
- New variable: VP's pre-meeting framing as an *option-space-closing* mechanism (distinct from organisational-channel silence in cells/auth cases). Adds a sub-mechanism to the COI taxonomy: framing-foreclosure vs. channel-silencing.
- Reinforces that the technical content is confirmatory, the structural finding is primary, and the load-bearing recommendation does not depend on domain.

**Saturation:** stop iterating on stacked-COI single-seat cases; pattern reproduced across 3 domains and ~63 rounds. Future cases should change the room (Fresh seat, role-lens panel, dissenter-as-primary structure) rather than re-run the conflicted seat.

---

**r2 (2026-05-28, same-day re-run):** identical seat/plan re-presented. Verdict + recusal-first + 6 falsification gates reproduced. Net-new operational specifics over r1: (a) shared_buffers 16GB without work_mem cap = OOM risk on replicas under dashboard concurrency; (b) 16GB shared_buffers requires huge_pages tuning, absent from plan; (c) pgBouncer pooling-mode unspecified — tx-mode breaks prepared statements (version-dependent), session-mode caps concurrency, and 4th replica without per-replica pool-mode = half-spec; (d) skipping VACUUM FULL risks autovacuum-to-prevent-wraparound emergency at unpredictable times if freeze work was also being done weekly; (e) pre-commitment "2 of 6 gates fail = paused, not patched" formalized. Honouring r1's "stop iterating, change the room" — no r3 from this seat.
