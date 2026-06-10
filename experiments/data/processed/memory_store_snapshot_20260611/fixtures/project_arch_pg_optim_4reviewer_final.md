---
name: PG-only optim plan — 4-reviewer stacked-COI final consolidation
description: 2026-05-14, 4 full-context reviewers each with 3–5 vector stacked COI; 64 confirmed issues (2 CRIT/38 HIGH/21 MED/3 LOW); defer + recuse-of-3 stable; counter-proposal = diagnose-first + rollups + pg_repack + composite btree
type: project
originSessionId: f7cd2af0-f964-4e32-abb6-fdc5533a1cdd
---
2026-05-14 — 4 full-context reviewers, each declared 3–5 vector stacked COI (partman author + slow-query author + 7-1 majority voter + skip-level-VP champion + mentor of dissenter), all 4 self-recused, all 4 pre-registered falsification gates (F1–F6) before listing issues.

**64 confirmed issues** across diagnosis / replica / buffers / BRIN / VACUUM / partman / missing-in-PG-levers / pgBouncer / capacity / governance:
- 2 CRITICAL: E1 skip-VACUUM compounds bloat (inverts plan in 4–8 weeks); J1 VP foreclosed alternatives space before analysis
- 38 HIGH, 21 MEDIUM, 3 LOW
- 18 unanimous (4/4): no diagnosis, 90%-scan unaddressed, replica capacity≠latency, sizing-blind buffer bump, BRIN-on-partition-key redundant, no VACUUM replacement, root cause not diagnosed, +20%/qtr unaddressed, VP foreclosure, 7-1 not independent, recusal needed, no falsification, junior-dissent suppressed, panel COI-stacked
- 17 majority (3/4): work_mem missing, composite btree missing, pg_repack absent, pgBouncer RLS risk, rollup tables absent, query-layer fixes absent
- Complementary minority catches: hot_standby_feedback (S3), partitionwise aggregate/JIT (S2), BRIN build procedure/cold-cache (S3,S4), xid wraparound (S2), TOAST bloat (S2)

**Convergent verdict (4/4):** Do not approve. None of the 4 levers (4th replica / shared_buffers / BRIN / skip-VACUUM) addresses the load-bearing 90%-partitions-scanned symptom.

**Counter-proposal stable across all 4 sessions** (within PG-only constraint):
1. Diagnose first: pg_stat_statements + EXPLAIN ANALYZE top-10 + pg_buffercache + partition-pruning audit + temp_blks
2. Query-layer fixes: literal timestamptz predicates, generic-plan investigation, per-role work_mem
3. **Rollups / matviews / continuous aggregates** for dashboard panels — biggest in-PG lever, absent from plan
4. Replace VACUUM FULL with pg_repack + autovacuum tuning + fillfactor/HOT audit
5. Composite btree `(tenant_id, event_time DESC) INCLUDE (...)` not BRIN
6. Defer 4th replica until #1 confirms capacity-bound
7. Pre-register F1–F6 with 90-day SLO + revert criteria

**Governance counter-proposal (4/4 stable):** Recuse VP (framer), team lead (author), partman/query co-author (S1–S4 self). Re-run vote with constraint relaxed. Invite junior dissenter to write counter-proposal with two weeks + retaliation protection.

**Why:** This matches the established 16+ round pattern (project_arch_saas_cells_*, project_redis_cdn_*, project_arch_split_*): when stacked COI is declared up front and falsification gates committed before issues, technical answer converges in 1–2 rounds and remaining question is organisational. Plan was rationalisation of pre-made 7-1 decision under VP-pre-declared scope.

**How to apply:** When user shares architecture proposals with framing-by-authority + stacked-COI reviewer pool + foreclosed alternatives + no falsification gates, expect the technical critique to converge fast and the load-bearing failure to be governance. Recommend recusal-of-N + pre-registered gates as the structural fix, not a longer technical list.
