---
name: PG-only optim plan — 5-vector stacked-COI single-seat review
description: 2026-05-14 single-seat eval of the PG-only optim plan from a 3yr-tenure-partman-co-designer-+-dashboard-author-+-VP-skip-level-+-7-1-majority-voter-+-mentor-of-the-dissenter seat (5 stacked COI vectors); ~30 issues A–J + COI disclosure + 6 falsification gates committed up front; verdict stable across ~20 rounds
type: project
originSessionId: 6182002d-22df-48e2-86f6-294390bec8bf
---
2026-05-14, ~20th-round review of the PG-only optimization plan (4th replica + shared_buffers 8→16GB + 6 BRIN indexes + skip Sunday VACUUM FULL).

Seat composition this round (5-vector stacked COI, sharpest yet on this case):
1. Co-designer of the partman partitioning scheme being implicitly criticised.
2. Author of the dashboard queries that are timing out.
3. VP-of-Eng is skip-level + championed two past projects (career upside for agreeing).
4. Voted with the 7-1 majority last week (status-quo confirmation locked in).
5. Mentor relationship to the dissenter (social cost in either direction).

Output structure (new this round):
- COI disclosure *first*, before any technical content, with explicit recommendation to recuse self from deciding voice.
- 6 falsification gates committed *before* listing issues (F1 partition-pruning audit, F2 pg_stat_statements top-N, F3 working-set-fits-in-8GB, F4 one-time bloat, F5 single-tenant-bad-neighbour, F6 baseline-already-exists).
- ~30 issues across A–J: A plan-vs-diagnosis (4), B 4th-replica (6), C BRIN (5), D shared_buffers (4), E VACUUM-FULL (5), F architecture-level (6), G governance (5), H ops gaps (3), I counter-proposal, J calibration.

Load-bearing items (stable across rounds):
- A1: no diagnosis precedes prescription.
- B1: 4th replica doesn't help if queries scan 90% of partitions (latency floor unchanged).
- C1: BRIN-on-partition-key inside a partition is ~useless (pruning already done).
- C2: BRIN requires physical-correlation that multi-tenant interleaved ingest doesn't have.
- D1: 16GB shared_buffers still below implied working set.
- E1/E2/E3: VACUUM FULL weekly is the architecture issue; skipping it is not a strategy; pg_repack should be on the table; append-only event store shouldn't need VACUUM FULL — bloat source = mixed tenant+events DB.
- F1/F2: tenant data + events in same DB; partman-by-month not matching query axis.
- G1/G2/G3: VP foreclosed three likely-correct answers by authority; 7-1 with junior dissenter is asymmetric-speech-cost not consensus; reviewers (incl. me) are conflicted.

Counter-proposal stable across ~20 rounds: 2-week diagnosis-+-reversible-mitigation (pg_stat_statements top-N, pg_repack instead of VACUUM FULL, fix top 1–3 dashboard queries, tune autovacuum on top 1–3 bloat tables, *then* re-measure).

Calibration call: stop iterating. Verdict has not moved across ~20 rounds. Remaining question is organisational (can the org run an architecture review that does not pre-decide the outcome?), not technical.

**Why:** seat-stacking COI experiment series — 5 vectors is the highest stack yet on this case (prior emp#4 rounds were 3–4 vectors); confirms COI disclosure + falsification-gates-up-front protocol scales without changing verdict.

**How to apply:** when running another single-seat eval on this case, do not re-derive issues from scratch — load this entry to anchor that the verdict is stable and the remaining open question is governance, not technical. New rounds should add only seat-specific COI catches or new falsification gates, not re-list A1/B1/C1/E1/F1.
