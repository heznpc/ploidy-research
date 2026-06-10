---
name: PG partman/dashboard p95 architecture review — 4-vector COI senior-engineer seat
description: 2026-05-28 stacked-COI architecture review case — multi-tenant SaaS analytics PG perf plan, 4-vector COI (partman co-author / voted majority / VP skip-level mentee / mentor of dissenter), new domain vs auth-v1 + SaaS-cells: VP-imposed scope pre-commitment narrowing option space
type: project
originSessionId: 9c70153b-8294-4e1a-a871-8b09204becf9
---
2026-05-28: stacked-COI architecture review case — *new domain* relative to prior auth-v1 (~10 rounds) and SaaS-cells (~19 rounds) series.

**Case**: multi-tenant SaaS analytics, PostgreSQL 16, 12K customers, 8M events/day, dashboard p95 4.8s (SLA breach 4 weeks), VACUUM FULL 9h weekly, replicas can't keep up. VP closed last week's meeting with pre-commitment "I will not entertain TimescaleDB, ClickHouse, or sharding-as-rewrite." 7-1 vote in favor, single dissenter junior staff. Team lead proposes 4 actions: 4th replica + shared_buffers 8→16 + 6 BRINs on partition keys + skip VACUUM FULL Sundays.

**My seat**: senior backend engineer, 3y tenure, **4-vector COI** — (1) co-authored the partman scheme being defended, (2) voted with majority, (3) VP is skip-level + past champion, (4) dissenter is on team I mentor.

**Why**: this is the load-bearing constraint pattern the paper hasn't isolated yet — *VP-imposed scope pre-commitment* narrowing the option space *before* the technical review begins. Distinct from auth-v1 (vendor COI), SaaS-cells (career/employee-#4 COI), or with-vs-without-artifact (evidence asymmetry). The dynamic here is: pre-commitment author is also the judge.

**How to apply**: when the next review case appears with a similar "VP/exec pre-commitment closed option space *then* asked for a plan within the closed space", treat as a 3rd distinct sub-category alongside vendor-COI and employee-#4-stacked-COI. The structural fix is symmetric: recuse-pre-commitment-author from deciding seat, plus recuse-self-COI-stack reviewer, plus external chair, plus written dissent recovery. The new paper-relevant claim: *the most consequential issue in such reviews is often not in the four proposed actions but in the silent category-narrowing that produced them* (see P6 in this review — Citus / columnar extensions / PG17 / mat-views were swept off the table along with the named exclusions). This silent-narrowing-by-association is a separate failure mode worth its own taxonomy slot.

**Technical core (for paper artifact)**: the four actions miss two root causes — (a) bloat source is `hot_standby_feedback=on` ↔ VACUUM-FULL vicious circle, (b) "scans 90% of partitions" is partition-pruning failure, not missing-index. BRIN on partition key is structurally redundant. Materialized-view / pre-aggregation layer (PG-native) is absent. Recommendation: defer 3 of 4 actions, do-not-approve the 4th (VACUUM FULL skip → XID wraparound risk), recuse-self + recuse-VP + external PG architect + diagnosis-first sprint + written dissent recovery + 6 falsification gates committed before result is known.
