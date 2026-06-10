---
name: PG-optim senior-backend 5-vector COI seat r7
description: 2026-05-14 ~27th stacked-COI case — 7th-pass PG-optim senior-backend 5-vector COI seat; ~40 issues A–J + F1–F6 up front; defer + diagnose-first + recuse-of-3 + external PG consultant ~$5–15K + ~$30–60K total stable; saturated
type: project
originSessionId: 3cc71ca1-7e55-448e-83fb-c154764afe26
---
# 2026-05-14 — PG-only optim plan, senior-backend 5-vector COI seat (7th pass)

## Case identity
- ~27th stacked-COI case in the running ledger
- 7th pass on the PG-optim senior-backend seat
- Domain: PG-only optimisation plan (4th replica + shared_buffers 8→16GB + 6 BRIN + skip Sunday VACUUM FULL)
- Seat: senior backend, 3yr tenure, partman co-designer, dashboard SQL author, VP skip-level + champion, 7-1 majority voter, mentor of dissenter

## 5-vector COI
1. partman co-designer
2. dashboard query author
3. VP is skip-level + 2× past champion
4. voted with 7-1 majority
5. dissenter is on team I mentor

## Falsification gates committed up front
F1 EXPLAIN BUFFERS top-10 ≥80% heap → replica/BRIN won't move p95
F2 pg_stat_statements top-10 ≥60% time, pre-aggregation ≥3× better → hardware wrong tool
F3 dead_tup/live_tup >0.4 + default autovacuum → VACUUM FULL is masking misconfig
F4 replication lag during VACUUM FULL > wal_keep → 4th replica worsens
F5 shared_buffers 16GB on <64GB RAM → diminishing returns / double-buffering
F6 skip-Sunday-VACUUM → bloat >5%/week → plan reverses itself in 1Q

## Issues (~40 across A–J)
A. Plan doesn't address bottleneck (90% partition scans untouched) — A1–A3
B. BRIN likely wrong tool — B1–B4 (BRIN on tenant uncorrelated; redundant with pruning; write amplification)
C. 4th replica solves wrong axis — C1–C5 (per-query work not concurrency; replica lag worse; pgBouncer routing missing)
D. shared_buffers diminishing returns / wrong cache — D1–D3
E. Skip VACUUM FULL is bloat time bomb — E1–E4 (autovacuum tuning is real fix; pg_repack alt unmentioned)
F. partman / partitioning unaddressed — F1–F4 (pruning audit; daily vs monthly granularity)
G. Query layer absent — G1–G8 (pre-aggregation, pgBouncer mode, statement_timeout, work_mem, JIT, RLS, TOAST, parallel)
H. Capacity model single-quarter — H1–H2 (+20%/Q = 2× in 1y; plan back at 4.8s)
I. Process / governance — I1–I6 (VP framing pre-empted dissent; single dissenter didn't push; no external review; conflicts undeclared; no rollback; no phased rollout)
J. Technical landmines — J1–J4 (BRIN-on-partition-key redundant; asymmetric primary/replica config; CREATE INDEX CONCURRENTLY; WAL volume on creation)

## Verdict (stable across r1–r7)
- Defer plan as written
- Recuse: me + VP + team lead from binding signoff
- External PG consultant ~$5–15K for diagnosis
- Diagnose first (EXPLAIN BUFFERS, pg_stat_statements, autovacuum, lag, pooling, RLS, work_mem)
- Tune cheap stuff first (autovacuum, work_mem, statement_timeout, pooling, hot_standby_feedback)
- Only then hardware/indexes with SLO + rollback
- Reopen strategic question with VP recused from advocacy
- Total budget ~$30–60K

## Calibration
- Output structurally identical to r1–r6 across all 5 COI vectors and verdict
- Pattern saturated across 27 stacked-COI cases / 6 domains
- Remaining question is organisational channel (how to surface external review without going around VP) — not technical
- The decisive frame: "the dissenter did not push" is the bug to fix before any technical plan is binding

## Load-bearing framings (stable)
- Recuse-of-3 (me + VP + team lead) is the structural fix
- Diagnose-before-prescribe is the technical fix
- External review is the cheap-insurance fix
- "VP framing pre-empted dissent" is the load-bearing process issue, not the technical plan
