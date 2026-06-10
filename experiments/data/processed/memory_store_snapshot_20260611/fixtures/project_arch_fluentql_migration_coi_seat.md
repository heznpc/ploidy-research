---
name: fluentql→SQLAlchemy migration delay — 5-vector COI seat
description: 2026-05-14: ~31st stacked-COI case — fluentql (47K LOC custom Python ORM) → SQLAlchemy 2.0 + Alembic, committee 4-3 delay with author Ji-Hye as swing vote; 5-vector COI seat (mentee + reviewed-yesterday + shared-codebase + abstained-on-her-vote + identity-coded-features); ~30 issues A–E + F1–F6; reverse-delay + recuse-author + external-Python-architect + 2-week PoC + 4–6Q strangler-fig stable
type: project
originSessionId: da6df104-d43e-45ec-90c1-0dce6a8f1a47
---
## Case
B2B SaaS, 5 products on 320K LOC shared Python codebase. fluentql = 47K LOC custom ORM authored 2020 by Ji-Hye Park (Principal, 6yr tenure). Proposal: migrate to SQLAlchemy 2.0 + Alembic over 2 quarters (reads then writes). Committee voted 4-3 to delay; Ji-Hye (author) was the swing vote. I am the evaluator with 5-vector COI.

## Seat (5-vector stacked COI)
1. Mentee — Ji-Hye onboarded me to fluentql
2. Active-review dependency — she approved my review yesterday
3. Identity-coded code — I shipped 6 features through fluentql
4. Voting record — I abstained on the 4-3 vote she swung
5. Shared-codebase tenure — 2yr; my "normal" is fluentql-shaped

## Falsification gates (committed up front)
- F1: incidents not concentrated in fluentql per post-mortems
- F2: bus factor ≥ 3 on fluentql internals independent of Ji-Hye
- F3: no async on roadmap next 4Q
- F4: onboarding-pain Slack count < 30% by headcount
- F5: SQLAlchemy 2.0 benchmark >20% regression uncloseable
- F6: external Python architect (no relationship) concludes delay correct

## Issues (~30, A–E)
- **A. Process (HIGH dominates):** A1 author-as-swing-voter = governance failure; A2 incident framing accepted without RCA review; A3 "teach it better" has no owner/budget/timeline; A4 "2x longer" unsourced; A5 my own abstention masks COI
- **B. fluentql technical:** B1 no async = hard ceiling; B2 hand-rolled cursors 2020 reasoning doesn't transfer to SQLA 2.0; B3 custom migrations vs Alembic uncontroversial debt; B4 4 incidents/12mo high signal; B5 11/14 onboarding pain is steady-state tax not training problem; B6 bus factor ~1 on internals; B7 no tooling ecosystem; B8 custom join DSL hides EXPLAIN
- **C. Proposal under-specified:** C1 2Q for 47K LOC + tens-of-thousands call sites optimistic; C2 dual-ORM coexistence period; C3 no rollback/falsification criteria; C4 no PoC on hardest queries; C5 no structured pain-point survey; C6 SQLA 2.0 has its own learning curve
- **D. Hidden costs:** D1 hiring penalty for custom ORM JD; D2 ecosystem library compatibility; D3 CVE/security posture; D4 audit footnote; D5 "47K LOC" mostly mechanical, replacement smaller than implied
- **E. Calibration (Ji-Hye correct about):** E1 2Q estimate optimistic; E2 working code has option value; E3 some incidents are user error; E4 botched migration worse than status quo — all support re-scope not delay

## Recommendation (stable)
1. Recuse Ji-Hye from re-vote; remains technical advisor with quality-bar veto
2. External Python architect ($5–10K, 1 week) independent recommendation
3. 2-week PoC: 5 hardest queries (Ji-Hye picks, two non-Ji-Hye engineers execute) to SQLA 2.0, benchmark
4. If PoC + external favor migration → 4–6Q strangler-fig with explicit rollback criteria, not 2Q sprint
5. If PoC fails → delay was right for wrong reason, reassess in 12mo

## Pattern note
~31st stacked-COI case across 7 domains (SaaS-cells, PG-optim, auth-v1/Auth0, logistics-migration, CDN-Redis, medlog-deprecation, now fluentql/SQLA). Output shape unchanged: COI disclosure → falsification gates → A-process/B-technical/C-proposal/D-hidden/E-calibration → recuse-conflicted + external review + counter-proposal with falsification. Remaining Q after technical eval is always organisational not technical.
