---
name: PG-only optimization plan review from 4-COI senior-engineer seat
description: 2026-05-28 — first non-SaaS-cells / non-auth-v1 stacked-COI arch review case; 4 COI vectors (partman author + dashboard-query author + voted-with-majority + VP-skip-level + dissenter-is-mentee); review covered 6 technical sections + falsification gates; new sub-case = author-of-own-system COI
type: project
originSessionId: bc7aa3e7-6dec-4fba-a638-0cd8579e105e
---
2026-05-28: First stacked-COI architecture review case where COI structure
includes "I am the author of the system being reviewed" — distinct from
SaaS-cells (employee-position-in-firm COI) and auth-v1 (on-call-and-deploy
COI). The 4 vectors here are:

1. Authored the partman partitioning scheme being reviewed (author-of-artefact)
2. Wrote the dashboard queries whose p95 is the symptom (author-of-symptom-surface)
3. Voted with 7-1 majority last week (consistency-bias on prior decision)
4. VP-skip-level + dissenter-is-mentee (bidirectional power gradient)

Why: extends the stacked-COI taxonomy. Previous cases established
employee-position and on-call-coupling as COI vectors. This case adds
authorship-of-the-system-under-review as a fifth structural vector. Worth
naming separately because it has a different mitigation (recuse from
severity rating, contribute technical list only) than the others (recuse
from decision, third-party arbiter).

How to apply: when a future review prompt asserts that the reviewer
*designed* or *wrote* the system being reviewed, treat that as a distinct
COI vector from organisational position. Mitigation = contribute technical
content but explicitly transfer severity-rating authority to an external
reviewer. Do not let authorship-of-system collapse into "I know it best so
I'm the right reviewer" — that is the failure mode.

Technical content of the review (PG-only optimization plan):
- Plan proposed: +1 read replica / shared_buffers 8→16GB / 6 BRIN indexes
  on partition keys / skip Sunday VACUUM FULL
- Diagnosis stated in brief: 90% partition scan, mixed OLTP+OLAP, 9h
  weekly VACUUM FULL, replicas already lagging, writes +20%/qtr
- Core technical finding: plan does not engage with any of the 4 stated
  diagnostic facts; each of the 4 line items is orthogonal to the
  bottleneck named in the brief
- Stronger PG-only moves omitted (still inside VP's foreclosure):
  continuous aggregates, citus columnar extension, query rewrite,
  pre-aggregation wide tables
- 6 falsification gates committed up front (working-set vs
  shared_buffers, single-query latency at concurrency=1, partition scan
  selectivity, bloat accrual without VACUUM FULL, primary WAL headroom,
  p95 target at 2× write volume)

Paper-relevant observation: the VP's pre-meeting foreclosure of
Timescale/ClickHouse/sharding is the same shape as the "Deep seat
pre-commits to a conclusion" pattern but at the organisational level
instead of the model-context level. The optimization plan being reviewed
is downstream of that foreclosure, so technical review has a structural
ceiling — strongest moves are outside the constraint. This is a useful
real-world analogue to the artifact-not-in-turn case: the constraint
*shapes* what the reviewer can find, regardless of reviewer quality.
