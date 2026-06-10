---
name: PG-optim 5-vector COI seat — round 4
description: 2026-05-14 ~23rd-round 5-vector-COI PG-optim seat; 4-vector + mentor-of-dissenter as 5th; ~35 issues A–J + F1–F6 gates up front; defer + diagnose-first + recuse-of-3 + external PG diagnostic ($5–15K) + ~$30–60K total stable; pattern stable across 23 stacked-COI cases
type: project
originSessionId: cafb0b2c-9e87-4047-a25e-8d08e70d03dd
---
2026-05-14 — ~23rd round in the stacked-COI single-seat series; 4th specifically on the PG-optim case.

**Seat composition (5 vectors):**
1. Partman partitioning co-designer (own-work invalidation cost)
2. Author of most-trafficked dashboard queries (queries-may-be-cause cost)
3. Skip-level report to VP who issued ex-cathedra closure
4. 7-1 voter (public commitment + face cost)
5. Mentor of the lone dissenter (5th vector — distinguishing this run from earlier PG COI seats)

**Output shape (now fully stable across cases):**
- COI disclosure as section 0, before any technical content, with "floor not ceiling" caveat
- 6 falsification gates (F1–F6) committed before listing issues
- ~35 issues across A–J (process / shared_buffers / 4th-replica / BRIN / VACUUM FULL / workload-shape / failure-mode / strategic / governance / self-flagged-COI-bias)
- Verdict: defer + diagnose-first + recuse-of-3 (author + VP + self) + external PG diagnostician + SLO-target + one-intervention-at-a-time + reopen-option-space
- Counter-proposal: $5–15K external diagnostic, then $30–60K + 4–8 weeks targeted fix (rollup tables, query rewrites, autovacuum re-tune)
- Closing "pattern call": remaining question is organisational, channel external to room that took 7-1 vote

**Load-bearing technical findings (stable across 4 PG-optim COI passes):**
- 90% partition scan is the load-bearing fact; partitioning likely not pruning → wrong key, wrong filter, or derived-column predicate
- Rollup/materialised-view absence is the highest-leverage miss
- BRIN on partition key is largely redundant (partition pruning already does it)
- VACUUM FULL weekly is symptom of autovacuum starvation; skipping defers not fixes
- 4th replica does not fix dashboard latency if bottleneck is per-query plan/sort/scan
- work_mem / sort-spill is the silent killer the plan never names
- Mixed OLTP+OLAP on one cluster is the structural mismatch the plan never names

**Load-bearing governance findings (stable across all 23 stacked-COI cases):**
- Pre-diagnosis option closure invalidates the vote
- 7-1 with coerced frame is compliance not consensus
- Lone dissenter's silence is room-data not conviction-data
- Author + decision-forcer + senior-IC-with-COI should not be sign-off authority
- External reviewer is the structural fix; not "more discussion" with same people
- Falsification gates must be committed before issue list, not after

**Confidence:** signal saturated. 23 cases, output shape stable, verdict stable, counter-proposal shape stable, structural fix (recuse + external review + falsification gates) stable. Calibration call: stop iterating on the technical side; the unknown is always the organisational channel.

**Distinguishing feature of this run:** mentor-of-dissenter as explicit 5th COI vector (not present in r1–r3); produced section J "things I want noted because my COI predicts I would underweight them" — self-flagged bias floor as a structural output element.
