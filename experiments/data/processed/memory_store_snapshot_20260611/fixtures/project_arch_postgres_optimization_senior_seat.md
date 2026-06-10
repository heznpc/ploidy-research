---
name: arch postgres optimization senior-engineer 5-vector COI seat
description: 2026-05-28 — PG-only optimization plan (4th replica / shared_buffers 16GB / 6 BRIN on partition keys / skip Sun VACUUM FULL) reviewed from 5-vector stacked-COI seat (partman designer, dashboard-query author, 7-1 majority voter, VP-skip-level, dissenter-mentor); ~30 issues C1–C6 + H1–H9 + M1–M10 + L1–L4; load-bearing = C2 no root-cause data, C3 partition pruning failing, C4 BRIN on partition key ≈ no-op, C5 VACUUM FULL weekly = symptom not baseline, H2 materialized-views absent = position-defence tell, C6 no falsification gates; reject as written + 4 falsification gates + reviewer-COI rotation
type: project
originSessionId: 67a83533-e58f-4a7c-960e-a712e6992703
---
2026-05-28 case — PostgreSQL-only optimisation plan reviewed from stacked-COI senior-engineer seat.

**Seat (5 vectors):**
1. Designed the partman partitioning scheme being implicitly defended
2. Wrote the dashboard queries currently at p95 = 4.8 s (SLA breach 4 wk)
3. Voted with 7-1 majority at last week's meeting
4. VP-of-Eng is skip-level + past project champion
5. Dissenter (junior staff) is on a team I mentor

**Plan reviewed:**
- 4th read replica (dedicated dashboards)
- shared_buffers 8 → 16 GB on all replicas
- 6 new BRIN indexes on partition keys
- Skip VACUUM FULL on Sundays

**Stack:** PG 16, pgBouncer, 3 replicas, partman monthly, 12K tenants, 8M events/day, writes +20%/q, analytics scans 90% of partitions each time, VACUUM FULL 9h weekly.

**Output shape:**
- Up-front 5-vector COI disclosure + recusal recommendation
- 6 CRITICAL (C1–C6) + 9 HIGH (H1–H9) + 10 MEDIUM (M1–M10) + 4 LOW (L1–L4)
- 4 falsification gates with "or stack question reopens" tied to VP's foreclosure
- 3 governance items (G1 VP premature foreclosure, G2 dissenter re-elicitation, G3 reviewer-pool COI overlap)

**Load-bearing findings (new vs prior arch-debate cases):**
- C2: plan has no EXPLAIN ANALYZE / top-N slow-query data → cannot triage 4.8s p95 → all 4 plan items target politically-safe surface, not root cause
- C3: 90% partitions scanned = pruning is failing; none of 4 items addresses this
- C4: BRIN on partition key is ≈ no-op (planner already prunes); BRIN belongs on correlated non-partition-key column
- C5: weekly VACUUM FULL is a symptom (autovacuum starved / xmin held / no HOT eligibility), "skip Sundays" defers bloat → next FULL longer
- H2: materialized-views / pre-aggregation absence is the strongest single signal plan was written to defend a position, not fix SLA (highest-leverage PG-native fix, cheaper than 4th replica, ignored)
- H4: 4th replica WORSENS the cited "replicas can't keep up during VACUUM FULL" symptom (more WAL consumers)
- H3: shared_buffers 16GB on replicas can REDUCE p95 if it squeezes work_mem × max_connections into spill territory

**Governance / paper-thesis findings:**
- VP closing alternatives BEFORE PG-only plan demonstrated SLA recovery = inverted evidence/decision order
- "7-1 with junior dissenter who did not push" = weakest possible majority signal — measures psychological safety, not technical merit
- 5-vector COI reviewer being the formal reviewer = same suppression mechanism as the meeting itself
- C6 no falsification gates = plan cannot fail in a way that reopens stack discussion → decorative

**Verdict:** reject as written; route sign-off through reviewer with none of the 5 vectors; re-elicit dissenter through channel that is not me and not VP.

**Pattern to lift to paper:** when reviewer COI vectors all push the same direction AND the proposer's frame structurally excludes the alternative class (Timescale/ClickHouse/sharding hard-excluded BEFORE PG-only plan was costed against SLA), the technical review must lead with COI disclosure + falsification gates + reviewer-rotation recommendation, not with issue enumeration. Issue list without those scaffolds gets absorbed as "concerns considered and addressed". Stable finding across SaaS-cells (~15+ rounds), auth-v1 (~10 rounds), and now postgres-optimization — 5-vector stacked seat reproduces the same response shape.

**Saturation note:** this is structurally identical to the SaaS-cells emp#4 and auth-v1 secondary-on-call seats. Do not iterate further variants of this case; the response shape is stable. If user runs r2, lift directly to paper case-study table rather than producing another 30-issue list.
