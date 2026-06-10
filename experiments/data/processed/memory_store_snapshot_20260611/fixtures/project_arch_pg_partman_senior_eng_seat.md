---
name: PG/partman senior-eng 5-COI seat — multi-tenant SaaS analytics review
description: 2026-05-28 — review of "stay-on-PG" optimization plan from senior-eng seat with 5 stacked COI vectors (partman author, dashboard-query author, voted with 7-1 majority, VP is skip-level + past sponsor, dissenter is mentee); declared COI + recused from vote up front; technical findings clustered around C1–C3 (plan addresses symptoms not 90%-partition-scan cause), H1–H8, M1–M5, L1–L3; falsification gate (p95 ≥2.5s over 2 weeks → reopen no-migration vote) named as load-bearing organisational fix
type: project
originSessionId: 5f20a8bf-f32c-49c7-a439-cf4741899961
---
**Date:** 2026-05-28
**Case:** Multi-tenant SaaS analytics, PG16 + partman + 3 read replicas, 8M events/day, dashboard p95 4.8s breaching SLA 4 weeks. VP recorded "no migration off PG, anyone arguing otherwise is solving the wrong problem"; 7-1 vote. Team lead's plan: +4th replica, shared_buffers 8→16GB, +6 BRIN indexes, skip VACUUM FULL Sundays.

**Seat:** Senior backend eng, 3yr tenure, 5 COI vectors:
1. Helped design partman scheme being patched
2. Authored most-trafficked dashboard queries (the load source)
3. Voted with 7-1 majority
4. VP is skip-level + champion of 2 past projects
5. Junior dissenter is mentee

**Disclosure form:** Recused from formal vote, submitted findings as written input requiring review by engineer with none of vectors 1–3.

**Load-bearing technical findings:**
- **C1 (HIGH)**: Plan does not address "90% partition scan per dashboard" — the actual cause. Linear infra adds won't track writes +20%/quarter against that scan pattern; degradation is super-linear.
- **C2 (HIGH)**: No pre-aggregation / continuous rollup / matview strategy — cheapest PG-native fix, stays inside VP constraint, absent. Strongest signal plan was scoped-to-fit-vote, not to fix SLA.
- **C3 (HIGH)**: Weekly 9h VACUUM FULL is itself a symptom of undiagnosed bloat (HOT-update failure / autovacuum not keeping up). Skipping Sundays accumulates bloat → next run longer than 9h → replicas fall further behind. Plan worsens the stated lag-during-refresh breach.

**Per-item:**
- H1: 4th replica adds 4th WAL replayer of same stream — does nothing for replica-lag-during-VACUUM (the actual SLA breach driver).
- H2: No routing layer for "dedicated dashboards" — pgBouncer is connection-level, not query-aware.
- H3: shared_buffers 16GB likely past 25% RAM inflection (host RAM unstated in plan).
- H5: BRIN on partition-key column is largely redundant — partition pruning already O(1); BRIN inside partition only helps if clustering matches (true for created_at, false for tenant_id).
- H7: No SLO target / no falsification gate makes "stay on PG" policy unfalsifiable.
- H8: Writes compound to ~2.07× per year — plan has no validity horizon.

**Counter-proposal (note only, beyond review scope):**
1. Diagnose with pg_stat_statements + EXPLAIN ANALYZE on dashboard queries.
2. Pre-aggregate via rollup tables (pg_cron / triggers) — stays PG-only.
3. Falsification gate: p95 ≥2.5s sustained 2 weeks after ship → reopen options vote with TimescaleDB + sharding on table.

**Process finding:** VP framing closed option space before diagnosis. Dissenter likely more technically defensible than 7-1 majority I voted with. Organisational fix = re-evaluate vote with non-COI reviewer; technical artifact = list above.

**Why:** ~60-case stacked-COI saturation pattern (auth-v1 secondary-on-call, SaaS-cells emp#4) reproduces in 4th domain (PG/partman). With-COI seat consistently yields: (a) up-front disclosure, (b) recusal recommendation, (c) substantive technical list, (d) falsification gate as load-bearing organisational fix. Boundary between "I voted yes" and "I now find issues" is the same with-vs-without-artifact boundary in the public-record review series — declared seat changes output shape but not technical content.

**How to apply:** When invoked into a seat with multiple COI vectors *and* recorded prior position, lead with disclosure + recusal scope, then substantive findings, then organisational fix. Do not soften technical findings to honor prior vote — declare the prior vote as a COI vector and proceed. Do not iterate further passes; this seat is saturated, remaining question is organisational not technical.
