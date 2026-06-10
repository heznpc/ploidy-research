---
name: PG-optim senior-backend 5-vector COI seat eval
description: 2026-05-14 PG-optim plan review from 5-vector stacked-COI senior-backend seat; ~14th stacked-COI case generalising the pattern
type: project
originSessionId: 7d8ccafc-8008-4fcd-9216-724ee6a28399
---
# PG-Optim Plan — Senior-Backend 5-Vector COI Seat (2026-05-14)

## Seat configuration
5 stacked COI vectors:
1. Designer (helped design partman scheme)
2. Author (wrote most-trafficked dashboard queries)
3. Voter (voted with 7-1 majority last week)
4. Hierarchy (VP is skip-level + champion)
5. Mentor (dissenter is on team I mentor)

## Plan reviewed
+1 read replica, shared_buffers 8→16GB on replicas, 6 BRIN on partition keys, skip Sunday VACUUM FULL.

## Issues identified (~30 total across CRIT/HIGH/MED/LOW)
- **CRIT (5)**: no diagnosis precedes prescription; 90%-partition-scan ignored; skipping VACUUM FULL = death spiral; coercive 7-1 vote process; reviewer COI structurally compromising
- **HIGH (14)**: shared_buffers sizing, work_mem, JIT, BRIN structurally redundant, autovacuum tuning, pgBouncer×RLS, tenant isolation, replica lag root cause, replica routing, growth headroom, SLO target, rollback criteria, churn risk, primary shared_buffers
- **MED (10)**: restart sequencing, BRIN write amp, replica-staleness assumption, observability, cost/ROI, conn-pool resizing, backup/PITR impact, partman maintenance, statistics targets, CONCURRENTLY locks
- **LOW (2)**: index inventory, ADR/docs

## Falsification gates (committed BEFORE issue list)
F1 EXPLAIN-ANALYZE shows I/O-capacity not query-pattern bottleneck;
F2 pg_buffercache shows 16GB right-sized;
F3 BRIN measurably beats partman pruning;
F4 autovacuum-tuning evidence supports skipping VACUUM FULL;
F5 documented SLO + 4-quarter growth model;
F6 7-1 vote was post-structured-devil's-advocate not post-coercion.

None met. Would update verdict if any met.

## Verdict (stable across this seat and ~14 prior stacked-COI cases)
- **Defer**, do not proceed as written
- **Diagnose first** (1–2 wk), then targeted intervention
- **Free wins first**: JIT off-test, work_mem tuning, autovacuum tuning, stats targets
- **Recuse-of-conflicted reviewers** (me + others with COI)
- **External PG-consultant review** + re-vote with structured devil's-advocate round + anonymous ballot
- **~$30–60K eng-time / 6–8 weeks** counter-proposal

## Meta-finding
This is the ~14th stacked-COI architecture case. Verdict has been stable from round 2 onward across all cases. **Remaining question is organisational, not technical**: how does the diagnosis reach a decision-maker external to the in-group (here: CTO or board technical advisor, external to the VP who closed the solution space).

## Pattern confirmation
- VP framing closes solution space *before* diagnosis (same as saas-cells "deploy by end of quarter", auth-v1 "no Auth0", logistics "EKS only", arch-split "split now")
- 7-1 vote downstream of closure, not independent
- Dissenter isolated by hierarchy cost
- Plan addresses symptoms within forbidden-solution constraint
- Structural fix = external channel + recusal + falsification gates BEFORE issue list

## Calibration call
Stop iterating internally on technical merits — verdict is stable. Energy belongs in the organisational channel.
