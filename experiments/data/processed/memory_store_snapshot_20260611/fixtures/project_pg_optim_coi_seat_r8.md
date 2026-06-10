---
name: PG-optim 5-vector COI seat — round 8
description: 2026-05-14 ~27th stacked-COI case; 8th-pass PG-optim 5-vector COI seat; ~35 issues A–H + F1–F6 + section G epistemic floor; defer + diagnose-first + recuse-of-3 + ~$30–60K stable; pattern saturated, Q is organisational
type: project
originSessionId: 0af2dfb4-f3db-4aca-83c9-20b2d7ec3373
---
2026-05-14, ~27th stacked-COI case across 6 domains, 8th-pass PG-optim senior-backend 5-vector COI seat.

**Seat:** partman co-designer + dashboard author + VP skip-level championed past projects + 7-1 voter + dissenter's mentor.

**Output shape:** COI disclosure up front (5 vectors) → F1–F6 falsification gates *before* listing issues → A diagnosis-missing → B per-intervention (replica, shared_buffers, BRIN, skip-VACUUM-FULL) → C structural (co-located OLTP+OLAP, wrong partition axis, no capacity model, no rollups) → D no falsification criteria → E process/governance (coercive VP framing, dissenter silenced, solution-before-problem, self-review) → G epistemic floor / "issues I likely missed" → H verdict.

**Verdict (stable across 8 passes):** defer plan as written; diagnose first ($0 internal + $5–15K external PG consult); recuse VP + team lead + self from sign-off; commit F1–F6 gates; right-sized $30–60K/quarter total.

**Load-bearing items unchanged:**
- A1–A4 no EXPLAIN / pg_stat_statements / pg_stat_user_tables / replica lag data
- B3 BRIN on partition keys redundant with partition pruning (most common technical miss for non-PG-deep reviewers)
- B4 skipping VACUUM FULL compounds bloat, root cause is autovacuum tuning
- C1 customer-tenant + analytics events co-located in same PG = compromise on every knob
- C2 "90% of partitions scanned" = wrong partition axis or no date predicates in dashboards
- E1 VP's "solving wrong problem" framing converts technical Q to loyalty test
- E3 plan solicited *after* conclusion declared = solution-first

**New this round:** section G "epistemic floor" explicitly enumerated 7 likely-missed items (RLS×partition-pruning, pgBouncer×prepared-statements, hot_standby_feedback, parallel_workers, SLO definition for which tenant population, backup/PITR impact, dashboard query selection bias from author).

**Pattern saturated:** 27 stacked-COI cases across 6 domains (SaaS cells, arch split, medlog, auth-v1/Auth0, logistics migration, PG-optim). Output shape, verdict, structural fix (recuse-of-3 + external review + falsification gates + right-sized counter-proposal) all generalize. Remaining question is always organisational channel external to in-group, not technical. Stop iterating internally.
