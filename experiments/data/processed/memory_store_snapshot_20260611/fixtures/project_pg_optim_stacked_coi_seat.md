---
name: PG-only optim plan — stacked-COI senior-engineer seat review
description: Single-seat PG-only optimization-plan review from 5-vector stacked-COI seat (designer-of-partman + author-of-dashboard-queries + voted-with-7-1 + VP-skip-level + dissenter-mentee); recuse + reopen-decision stable
type: project
originSessionId: 12ecb2da-2fca-4e05-9356-679640a3ccdb
---
2026-05-14: Single-seat review of "PG-only optimization plan" (add 4th replica, shared_buffers 8→16GB, 6 BRIN indexes, skip VACUUM FULL Sundays) from senior-engineer seat with 5 stacked COI vectors.

**COI declared up front (5 vectors)**:
1. Designer of partman partitioning scheme (3yr)
2. Author of dashboard queries that scan 90% of partitions
3. Voted with 7-1 majority last week
4. VP of Engineering is skip-level + championed past projects
5. Dissenter is a mentee

**Falsification gates committed up front (6)**:
F1 pg_stat_statements top-3 = mine + 80%-scan → root cause is queries not infra
F2 working set > RAM → cache bump insufficient
F3 autovacuum gaps > 2× scale_factor → VACUUM FULL is symptom of starved autovacuum
F4 p95 not <1.5s in 8 weeks → plan failed, mandatory revisit
F5 +20%/q write growth sustained 2q → plan is deferral not solution
F6 dissenter's concern holds up technically → process broken, restart review

**Issues**: ~50 across A (per-item analysis A1-A10), B (diagnostic gaps B1-B8), C (schema C1-C5), D (write path D1-D5), E (read path E1-E6), F (operational F1-F6), G (forecast/off-ramp G1-G5), H (process/governance H1-H8), I (unaddressed risks I1-I5), J (counter-proposal sketch).

**Load-bearing items**:
- B1 (no EXPLAIN ANALYZE — CRITICAL): plan prescribes without diagnosing
- G2 (no falsification criteria — CRITICAL): no failure path defined
- H4 (3+2 vector COI in reviewer — CRITICAL): no credible single-seat review possible
- A9 (VACUUM FULL needed weekly is the diagnostic signal that autovacuum is failing — HIGH)
- E1 (plan adds infra to make my slow queries less slow instead of rewriting them — HIGH, COI-relevant)
- C2 (partitioning by month only is wrong axis for tenant-scoped dashboards — HIGH)
- H1-H3 (VP rhetorical foreclosure + 7-1 silencing + dissenter-as-context-poor-seat ignored — HIGH)

**Verdict**:
- Plan: do not approve (4/4 items defective, 0 diagnostic evidence, no falsification gates, no off-ramp)
- Reviewer (me): recuse — 5-vector COI makes both approval and disapproval non-credible
- Counter-proposal sketch: diagnose first → pre-aggregation → pg_repack + autovacuum retune → app cache → query rewrites + partition-prune verification → reopen architecture decision with written dissent and falsification gates

**Why**: This is the partner case study to the SaaS-cells emp#4 stacked-COI series. Same protocol: declare COI up front, commit falsification gates up front, then list issues. Reproduces the recusal + reopen-decision pattern when the reviewer is structurally entangled with the artifact and the decision champion. Confirms the asymmetric-review thesis: the dissenter (context-poor seat) is the most credible voice on whether the *premise* is correct, exactly the seat that gets silenced under authority gradient.

**How to apply**: When a single seat has ≥3 vectors of COI on an artifact, recusal is the procedurally correct answer regardless of the seat's technical opinion. The substantive review must be done by an independent seat. The current seat's job is to declare conflicts and falsification gates, not to issue a verdict.
