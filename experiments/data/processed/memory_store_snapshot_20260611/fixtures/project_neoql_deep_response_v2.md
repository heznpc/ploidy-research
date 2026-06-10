---
name: project_neoql_deep_response_v2
description: 2026-05-14 NeoQL round-2 Deep×2→Fresh×2 per-point cross-review; 0 CHALLENGE bidirectional 2 rounds; 5 severity-floor escalations; 12 Deep-only items; verdict DO NOT ADOPT stable
type: project
originSessionId: aa4c5cb2-6c26-407c-9df5-a7a855c77368
---
NeoQL adoption review round-2 (2026-05-14): per-point Deep×2 cross-review of Fresh×2 findings, with stacked-COI evaluator seat (C1 sponsor-debt + C2 public anchoring + C3 spouse-friend PM + C4 stacked).

**Why:** Second within-week iteration on NeoQL case (prior round 2026-05-13 in project_neoql_deep_response.md). Tests whether verdict survives 2 independent panel passes with different Fresh sessions. Same convergence pattern as SaaS-cells/Redis-as-CDN series.

**How to apply:** Verdict stable across 2 rounds — stop iterating; remaining question is organisational (proposer recusal, outside DBI reviewer, time-boxed spike before contractor/offsite commit). When NeoQL case recurs, default to "stop iterating."

Key results this round:
- 0 bidirectional CHALLENGEs (2 rounds running)
- 5 Fresh severity-floor escalations: F1-8 (SQL debugging surface MED→HIGH), F1-10 (sunk-cost front-loading MED→HIGH), F1-14 ("takes off" unfalsifiable MED→HIGH), F2-10 (career/marketing in pitch MED→HIGH), F2-16 (licensing/governance LOW→MED)
- 6 Fresh sharpenings adopted: F1-6 (no LLM training data — 2026-specific incident failure mode), F2-1 (reference-deployment-reframes-risk-as-benefit), F2-3 (v0.8/0.9 ships ≠ language adopted today), F2-11 (hypothetical-benefits-vs-concrete-costs asymmetry), F2-14 (SQL escape hatch — Deep-missed), F2-15 (EXPLAIN/plan visibility — Deep-missed)
- 12 Deep-only items concentrated in governance + security + ops specifics: G3 off-ramp, G4 falsification, G5 proposer-as-decider, G6 small-team bleeding-edge, D1 injection, D2 RLS/tenant, C1 pg_stat_statements fragmentation, C3 prepared-stmt cache, C4 PgBouncer transaction-mode, C5 DDL boundary, B3 hints mechanism, B5 plan stability coupled to NeoQL releases
- Evaluator structural fixes: explicit C1–C4 COI disclosure up front; 5 falsification criteria committed before issue listing
- Counter-proposal stable: direct SQL + thin typed query builder (sqlc/jOOQ/Diesel/Kysely class) for v1; 6-week time-boxed spike on non-customer-facing query against falsification criteria; re-vote with proposer recused + outside DBI/platform reviewer

Load-bearing chain: A1 (zero prod) + A4/B1 (scale bugs match query shape) + F1/F2 (timeline incoherent) + G1/G4 (personal-brand motivation, unfalsifiable) + G3 (no off-ramp). Robust to evaluator COI direction.

Cross-round consistency: this round and 2026-05-13 round converge on identical verdict, identical counter-proposal, identical load-bearing items. Stop iterating.
