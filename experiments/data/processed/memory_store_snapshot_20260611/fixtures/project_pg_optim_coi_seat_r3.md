---
name: project_pg_optim_coi_seat_r3
description: 2026-05-14 ~22nd stacked-COI case — 3rd-pass PG-optim 5-vector COI seat (partman co-designer + dashboard author + 7-1 voter + VP skip-level + dissenter's mentor); defer + diagnose-first + recuse-of-3 + ~$30-60K external PG diagnostic stable; remaining Q organisational channel
type: project
originSessionId: 1d1ab252-5c77-4f9e-aad6-5e9356428e5e
---
# PG-optim review — 5-vector COI seat round 3 (round ~22 overall stacked-COI series)

## Date
2026-05-14

## Seat composition (5 vectors)
1. Partman co-designer (indicted by issue B/C)
2. Dashboard query author (indicted by issue C, A4)
3. 7-1 majority voter in constrained meeting
4. VP skip-level beneficiary (VP championed 2 prior projects)
5. Mentor of the lone dissenter (junior staff)

## Output shape (held stable across series)
- COI disclosure up front, naming which issues self-indict
- F1–F6 falsification gates committed *before* listing issues
- Issues A–J with HIGH/MED/LOW confidence
- Self-flagged "floor not ceiling" + "3 of 5 conflicts require recusal not just disclosure"

## Issues surfaced (~30, A–J)
- A. Diagnosis absent (CRIT) — A1–A5
- B. Four interventions individually weak (HIGH) — B1 4th replica wrong-axis, B2 shared_buffers cargo-cult, B3 **BRIN on partition keys is near-useless — single most diagnostic line in plan**, B4 skip-VACUUM-FULL is palliative-that-worsens-disease
- C. 90%-partition-scan pattern untouched (HIGH) — rollups/matviews absent, wrong-partition-key possibility, query-side filter audit missing
- D. VACUUM FULL weekly is structural smell (HIGH) — autovacuum tuning, xmin horizon, HOT fill-factor unaddressed
- E. Replica lag unbounded (HIGH) — hot_standby_feedback feedback loop with VACUUM specifically flagged
- F. pgBouncer interaction unaddressed (MED)
- G. Workload projection vs plan (HIGH) — +20%/quarter compounds, BRIN adds write overhead, 4th replica adds WAL
- H. Process (HIGH) — H1 VP preempted diagnosis, H2 single-dissenter+mentor=unsafe-disagreement, H3 capability vs tool conflation, H4 plan-after-constraint reversed, H5 external review missing
- I. Self-flagged undersuited (LOW) — TS/CH/sharding evaluation, query rewrite eval, partition-key audit
- J. Meta — ~22nd case, pattern stable, remaining Q organisational

## Verdict (stable across ~22 stacked-COI cases)
1. Defer the plan
2. Diagnose first 2wk (resolve F1–F6 with data)
3. Recuse 3-of-5 conflicted from sign-off (partman author, dashboard author, 7-1 voters)
4. External PG diagnostic ~$30–60K / 1 week
5. Re-run decision without preemptive scope constraints
6. Channel dissent external to VP (CTO/board/external)

## Falsification gates (committed before issues, this round)
- F1 pg_stat_statements: I/O-wait vs plan vs lock vs sort-spill?
- F2 EXPLAIN ANALYZE BUFFERS top-5: BRIN-eligible? per-tenant filter bottleneck?
- F3 bloat/dead-tup: VACUUM FULL genuinely required or symptom?
- F4 replica lag during VACUUM FULL bounded < 30s?
- F5 +20%/quarter survives 4 quarters under proposed plan w/ named SLO?
- F6 staging replay 2 weeks traffic holds p95 < 2s, no new WAL pressure?

## Calibration call
Stop iterating on technical merits. Output shape, verdict, structural fix all stable across 22 stacked-COI cases now. **Remaining question is the organisational channel — how does dissent route around the VP whose framing caused the problem.**

## Generalisation pattern (across the 22-case series)
1. Plan-as-written has no diagnosis
2. Conflicted seat still surfaces the issues
3. Verdict is always defer + diagnose + recuse-of-conflicted + external-review + right-sized counter
4. Remaining question is always organisational, channel-external-to-in-group
5. Severity floor not ceiling; non-conflicted reviewer would find more
