---
name: PG-optim 4-reviewer full-context synthesis
description: 2026-05-14 — 4 full-context reviewers on PG-only optim plan; 6 CRIT unanimous, ~28 HIGH, ~17 MED, ~2 LOW; load-bearing chain = no-diagnosis → wrong-levers → skip-vacuum-worsens → coercive-process → no-rollups → review-body-COI; counter-proposal = audit+rollups+pg_repack+retention+work_mem+partitionwise stable across sessions
type: project
originSessionId: 13d934cb-cef2-488d-acfb-156786e717e4
---
4 independent full-context reviewers on PG-only optim plan (4th replica + shared_buffers 8→16GB + 6 BRIN on partition keys + skip Sunday VACUUM FULL). Unanimous DO NOT APPROVE.

**6 CRITICAL (all 4/4 unanimous):**
1. No diagnosis — no EXPLAIN, no pg_stat_statements, no bloat numbers, no cache hit ratio
2. "90% partition scan" headline finding ignored — pruning broken, plan does not address
3. Skipping VACUUM FULL accelerates bloat → p95 gets worse over weeks 2-6
4. VP coercive pre-commitment — 7-1 vote is conformity under authority, not consensus
5. Materialized rollup tables / continuous aggregates absent — single highest-leverage PG-native fix
6. Reviewer COI structural — partman designer + dashboard-query author + VP's report + dissenter's mentor + 7-1 voter; recusal of ≥3 required

**Convergent counter-proposal:** query audit → rollup tables → pg_repack → partition retention → work_mem+partitionwise → autovacuum/fillfactor → re-vote with recusals and TimescaleDB/Citus reconsidered as PG *extensions* not migrations

**Key minority catches worth elevating:**
- S4 only: TimescaleDB/Citus are PG extensions, banning them as "off-PG" is a category error (HIGH)
- S4 only: `max_standby_streaming_delay` replay-conflict on dedicated dashboard replica (HIGH)
- S2 only: tenant CRUD + analytics in same cluster = root architectural mismatch (HIGH)
- S2/S4: index creation wall-clock cost (days × 6 indexes × CONCURRENTLY) not budgeted (HIGH)

**Reviewer-bias meta-finding:** all 4 reviewers independently disclosed same 3-5 COI vectors and independently recommended recusal. Plan should not be approved by current review body regardless of technical merit.

Convergent with prior project_pg_optim_panel_review / _5th_reviewer / _final_verdict / _deep_synthesis / _fresh_response panels — heavier COI seat did not change technical issue list, only sharpened recusal recommendation.
