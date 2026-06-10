---
name: PG scaling plan review — stacked COI seat r3
description: 2026-05-28 — 3rd same-day variant of PG/partman stacked-COI architecture review; ~26 issues 7 categories; saturated, do not iterate further unless structurally novel seat or domain
type: project
originSessionId: 59d7493d-dc7e-4030-817f-176ab69c16f2
---
2026-05-28 — **r3** of the same-day PG/partman/stacked-COI architecture-review case. Prior:
- r1 = `project_arch_pg_saas_analytics_stacked_coi.md` (16 issues, 4/5/5/1 severity, recuse + external chair)
- r2 = `project_arch_pg_partman_seat_with_artifact.md` (3 CRIT + 5 HIGH + 6 MED + 2 LOW + 5 falsification gates; VP foreclosure-before-analysis lifted as process-level architecture risk)
- r3 = this entry — ~26 issues across 7 categories (Index / Memory / VACUUM / Replication / Pooling / Growth / Process); load-bearing L0 = "90% partition scan unaddressed"

**Same seat across r1–r3**: 3-yr senior backend eng; co-designed partman; wrote dashboards; voted 7-1; VP=skip-level/champion; dissenter=mentee.

**Same plan reviewed**: 4th read replica + shared_buffers 8→16GB + 6 BRIN on partition keys + skip Sunday VACUUM FULL.

**What r3 added vs r1+r2** (modest, but not zero):
- Surfaced BRIN-summary lag (autovacuum BRIN-summarize cadence) as #2
- Surfaced hot_standby_feedback vs max_standby_streaming_delay tradeoff on the new dashboard replica (#15) — long analytics queries either get cancelled or pin VACUUM on primary
- Surfaced pgBouncer transaction-mode vs prepared-statements as silent latency tax (#16)
- Surfaced fillfactor / HOT path interaction with weekly VACUUM FULL need (#11)
- Reframed VP's pre-vote constraint as "defensible content, inverted timing" rather than as a frame to override

**What stayed identical across r1–r3** (structurally saturated):
- 5-vector COI disclosure first
- L0 = 90% partition scan as load-bearing
- weekly VACUUM FULL as symptom not schedule
- BRIN-on-partition-key as category error
- 4th replica = 4th lagging dashboard
- write +20%/q ignored
- recommendation = pause + 2-week diagnostic + falsification gates + re-vote with external chair + recuse-of-3

**How to apply**: PG/partman stacked-COI variant is now 3-deep on same day; same seat + same plan saturates at ~25 issues. Do not run r4 of the identical seat. If a structurally novel variant arrives (different domain like Knight Capital, or a fresh non-author seat reviewing the same plan, or VP himself as the seat), it can run; otherwise stop. Lift the constraint-frame-as-load-bearing-risk and reviewer-as-author-as-disqualifying findings to the paper case-study slot — these are the only structural deltas vs the SaaS-cells / auth-v1 series.
