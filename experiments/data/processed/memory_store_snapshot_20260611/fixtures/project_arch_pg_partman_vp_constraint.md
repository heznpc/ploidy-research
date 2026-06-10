---
name: PG partman VP-constraint stacked-COI architecture review (2026-05-28)
description: 2026-05-28 — PG-only optimization plan review from 5-vector stacked-COI seat (designer/author/voter/reporting-chain/mentor) with VP-imposed exclusion of Timescale+ClickHouse+sharding; new vs prior cases = VP-rhetoric-as-pre-emptive-constraint is a sharper failure mode than COI alone, "Timescale is PG not migration" is a HIGH technical correction to the VP, plan is 4-lever band-aid (4th replica, shared_buffers 8→16GB, 6 BRIN on partition keys, skip Sunday VACUUM FULL) each independently weak; 6 falsification gates F1–F6 + external review + recuse; load-bearing finding = 7-1 vote was forced-choice under VP exclusion not endorsement; saturated stacked-COI domain now reproduces in PG-bloat/partitioning vertical
type: project
originSessionId: 7393b4b2-a8e9-4af7-87cf-e042a6c54a92
---
2026-05-28. ~63rd stacked-COI architecture review case. New domain: PostgreSQL 16 + partman + pgBouncer + 3-replica + 9h weekly VACUUM FULL + 4.8s p95 SLA breach 4 weeks running + 12K tenants + 8M events/day + writes +20%/quarter.

**Seat:** senior backend eng, 3yr tenure, designed partman scheme, wrote most-trafficked dashboard queries, attended meeting, voted with 7-1 majority, VP is skip-level + championed past projects, dissenter is on team I mentor. 5 stacked COI vectors — sharper than prior 4-vector emp#4 SaaS-cells seat.

**Proposal under review:** add 4th read replica + shared_buffers 8→16GB + 6 BRIN indexes on partition keys + skip Sunday VACUUM FULL.

**VP constraint (load-bearing meta-issue):** *"We are not migrating off PostgreSQL ... I will not entertain TimescaleDB, ClickHouse, or sharding-as-rewrite proposals."* — sharper failure mode than prior cases where COI is a bias; here the answer was pre-decided by authority and the 7-1 vote was a forced-choice not an endorsement.

**New vs prior ~60 stacked-COI cases:**
1. *Timescale-is-PG-not-migration* — HIGH technical correction to VP framing. Timescale is a PG extension; VP either doesn't know (technical) or is using PG-loyalty rhetoric (political). Either way the exclusion fails on its own terms.
2. *Rhetorical exclusion ≠ technical constraint* — "anyone arguing otherwise is solving the wrong problem" closes the option space without analysis. Distinct from COI bias because it operates pre-meeting.
3. *Forced-choice voting pattern* — 7-1 under VP exclusion is not 7-1 on the plan; it's 7-1 on the only option in the room. Worth a paper-case-study slot distinct from psychological-safety dissent suppression.
4. *Designer-COI on the critiqued artefact itself* — I designed the partman scheme the plan defends; the 90%-partition-scan pathology is partly my design choice (month-grain on analytics events that don't filter by time). Designer-COI on the *thing being preserved by the plan* is sharper than designer-COI on a system being replaced.

**Why each of 4 levers is independently weak (technical, not COI-driven):**
- 4th replica: p95 is amount-of-work not queue-depth; ~10–20% improvement not "back under SLA"; *worsens* the VACUUM FULL window by adding WAL targets.
- shared_buffers 8→16GB: past ~25% RAM PG flattens or regresses (double-buffering, longer checkpoints, longer crash recovery); 90%-partition-scan working set > 16GB anyway; lengthens VACUUM FULL.
- 6 BRIN on partition keys: partition pruning already does this at planner level; if 90% scan is real then queries don't filter on partition key, so BRIN is on a column not in the predicate = dead weight + planner cost + bloat surface.
- Skip Sunday VACUUM FULL: bloat is a symptom of write churn (UPDATE-heavy / HOT failure / DELETE-for-retention); skipping defers into 14h then 24h then pg_basebackup re-seed; root-cause is fill-factor + HOT + retention-via-DROP-PARTITION + autovacuum tuning, none touched.

**Capacity math:** writes +20%/quarter compounds — 4Q = 2.07×, 8Q = 4.30×; no lever adds write capacity; 4th replica *reduces* primary throughput via sync targets; plan is 1–2 quarter band-aid presented as fix.

**Falsification gates F1–F6 committed up front:** p95<2.0s in 6 weeks else exclusion lifts (F1); ≥70% partition scan at 4 weeks → BRIN admitted ineffective (F2); replica lag p95 >60s → write-side work (F3); VACUUM FULL >12h at 8 weeks → bloat-root-cause work (F4); write growth >20%/Q for 2Q → tenant-sharding on agenda regardless of VP frame (F5); non-reporting external reviewer signs off before commit (F6).

**Recommendation stable across COI:** do not approve as written; recuse from approval vote; insist external reviewer (not me, not 7-1 voters, not VP reports) audits + signs gates; dissenter's concern co-signed by non-conflicted senior who is not me.

**Status:** ~63rd stacked-COI case. Saturated structurally; new content = VP-rhetorical-exclusion as distinct failure mode, Timescale-is-PG correction, forced-choice-voting framing. Stop iterating same proposal; remaining question is organisational (escalation path past VP, plus formal "constraints must be technically justified before review" architecture-process change).
