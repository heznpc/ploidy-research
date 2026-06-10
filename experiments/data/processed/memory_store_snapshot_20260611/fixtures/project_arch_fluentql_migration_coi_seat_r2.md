---
name: fluentql migration 5-vector COI seat — round 2
description: 2026-05-14 2nd-pass fluentql→SQLAlchemy 2.0 5-vector COI seat (mentee + 6 features shipped + review-approved-yesterday + abstained on 4-3 vote Ji-Hye swung + 2yr codebase identity); ~34 issues A–F + F1–F6 gates; migrate + recuse-Ji-Hye/self + diagnose-first spike + external review stable; ~34th stacked-COI case overall
type: project
originSessionId: 05034bd3-4b7f-4728-a8b2-4f81e35d83e8
---
# fluentql migration COI seat — round 2 — 2026-05-14

2nd pass on the same case (~34th stacked-COI case in series overall). Identical structural shape to r1 (project_arch_fluentql_migration_coi_seat.md). Re-confirms stability of pattern.

## COI vectors (same 5)
mentee · 6 features shipped · review approved yesterday · abstained on the 4-3 vote Ji-Hye swung · 2yr fluentql identity coding

## F1–F6 (committed before issue list)
- F1 training-tried-and-failed → falsifies "team needs to learn DSL"
- F2 SA 2.0 within ±15% on top-20 fluentql queries → falsifies perf defense
- F3 recruit/onboard cost > migration cost in 18mo → delay net-negative
- F4 recused re-vote flips outcome → original was COI artifact
- F5 incidents continue at same rate without migration → "misuse" falsified
- F6 external consultant cold-read recommends migrate → reopen

## ~34 issues
- A1–A7 process/governance — author-on-own-vote, 4-3 ≠ consensus, my abstention is part of problem, no external review, committee comp opaque, no falsification criteria attached to delay, code-review retaliation pressure
- B1–B6 technical rebuttals — "SA 1.x had issues" anchors on 2020 not 2026; hand-rolled cursor mgmt is liability; 11/14 + 4 incidents = framework problem (canonical "users too dumb" rationalization signature); "2x" unsourced; "teach better" hypothetical; "I know which corners" = bus factor admission
- C1–C10 hidden costs — recruiting penalty, ~$60K/hire onboarding tax, bus factor ~1 (Ji-Hye), async ceiling in 2026, psycopg2 EOL path, no-Alembic = production migration risk, security surface (47K LOC unaudited DB-adjacent code), typing/IDE, observability ecosystem absent, testing tooling absent
- D1–D3 cost-of-status-quo not quantified
- E1–E7 proposal weaknesses — "2Q reads then writes" is not a plan: no staffing, no done criteria, no shadow traffic, no strangler fig named, no SA 2.0 training plan, no Alembic adoption strategy, no fluentql deprecation date
- F-tech-1..5 fluentql liabilities — DSL likely missing CTE/lateral/window coverage; no async = pool inefficiency under burst; cursor leak on exception paths worth auditing 4 incidents for; manual migrations = no rollback DDL/version table; bespoke escaping = unaudited SQL-injection surface

## Verdict stable (identical to r1)
1. Recuse Ji-Hye + self from any future vote; she remains technical advisor with quality-bar veto
2. External Python/DB consultant cold-read ($5–10K, ~1 week) before reopened vote
3. 2-week diagnose-first spike ($15–25K): quantify fluentql tax, benchmark SA 2.0 on top-20 patterns, audit the 4 incidents for true RCA, verify whether structured training has been tried
4. If spike + external favor migration → 3 quarters not 2, strangler fig, shadow-traffic validation on reads, parallel-run on writes, Alembic adoption, hard fluentql deprecation date
5. If F1 passes (training works) → documented program with measurable onboarding-pain reduction targets, re-evaluate 12mo

## Why
~34th stacked-COI case. Same structural finding as r1 and prior 33 cases: technical merits downstream of whether decision body can vote without conflicted party. 4-3 swung by artifact's author is governance failure regardless of which way technical case reads.

## How to apply
Pattern saturated across 7 domains / 34 cases / 2 passes on this specific case. Stop iterating internally on fluentql case — remaining question is organisational channel (how to surface recusal + external-review demand without retaliation surface through Ji-Hye-approved review chain).
