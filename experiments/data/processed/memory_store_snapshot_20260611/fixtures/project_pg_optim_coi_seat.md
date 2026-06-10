---
name: PG-optim plan single-seat eval (4-vector COI)
description: 2026-05-14 single-seat review of PG-only optim plan (4th replica + BRIN + shared_buffers + skip VACUUM FULL) from 4-vector stacked-COI seat (partman designer + VP-skip-level + dissenter-is-mentee + yes-voter); ~40 issues across A–F; coercive VP decision named as load-bearing
type: project
originSessionId: 647ba742-035f-4283-ac03-83794ffdf361
---
2026-05-14 — Single-seat review of the team-lead's PG-only optimization plan, taken from a 4-vector stacked-COI seat:

1. designer of the partman scheme being extended (sunk cost)
2. VP-of-Eng is skip-level, has championed past projects
3. junior dissenter is on a team I mentor
4. I voted with the 7-1 majority

**Structural pattern reused** from the SaaS-cells / Redis-as-CDN series:
- COI disclosure declared *before* listing issues
- 6 falsification gates committed up front (F1–F6)
- Verdict offered as input, not conclusion (because seat is COI-compromised)
- Recusal of 3+ reviewers proposed as structural fix

**Issue catalogue** (~40 items across 6 categories):
- A. Diagnosis missing — no EXPLAIN/pg_stat_statements; "scans 90% of partitions" buried as context, not flagged as root cause; no SLO target.
- B. The four interventions individually:
  - B1: 4th replica doesn't fix per-query latency
  - B2: makes replication lag worse during VACUUM FULL
  - B3: BRIN on "partition keys" is structurally redundant
  - B4: BRIN needs physical correlation — fails on tenant_id etc.
  - B7: skipping VACUUM FULL suppresses maintenance, doesn't remove the need
  - B8: weekly VACUUM FULL itself signals autovacuum mistuning
  - B9: 6 indexes add write amplification at +20%/quarter growth
- C. Workload mismatch — OLTP/OLAP co-tenancy; raw-event dashboard primitive; partitioning provides ~0 pruning benefit at 90% scan rate
- D. PG-native levers ignored — autovacuum tuning, work_mem, partitionwise aggregate/join, JIT, pg_repack, per-partition VACUUM FULL, TOAST scan cost, covering indexes
- E. Ops gaps — read routing through pgBouncer undefined, replication-lag staleness vs SLA, failover, connection pool sizing, cost not quantified
- F. **Process/governance — load-bearing**: VP pre-empted solution space ("will not entertain TimescaleDB/ClickHouse/sharding"); 7-1 vote with junior dissenter who "did not push" = information cascade; no measurement gate; no falsification criteria; reviewer pool not COI-clean (≥3 yes-voters have structural bias toward stay-on-PG); decision asymmetry favors investigation but went the other way

**Verdict**: Do not approve as written. Block until diagnostic data exists; re-scope to rollups + autovacuum tuning + pg_repack + work_mem before spending on replica/BRIN; recuse ≥3 conflicted reviewers (incl. self) and re-vote; reopen rollup/columnar branch for *evaluation only*.

**Why this matters for the paper**: Adds a new template iteration — same context-asymmetric single-seat protocol applied to a PG-optim domain instead of arch-rewrite. 4-vector COI is the new variant (designer + skip-level + mentor + voter). Confirms that the "declare COI + falsify up front + recuse-of-N" structural fix transfers across domains.

**How to apply**: When future PG/optimization plans land with a pre-anchored exec position and a uniform vote, treat the *process* as the load-bearing issue (per F5/F6 pattern) and propose recusal-of-conflicted before re-engaging on technicals.
