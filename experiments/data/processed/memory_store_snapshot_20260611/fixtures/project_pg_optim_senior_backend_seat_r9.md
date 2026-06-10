---
name: PG-optim senior-backend 5-vector COI seat — round 9 (~29th stacked-COI pass)
description: 2026-05-14 — 9th-pass PG-optim senior-backend seat (~29th stacked-COI case overall / 9th domain). Output structurally identical to r1–r8. Verdict + counter-proposal saturated.
type: project
originSessionId: 095d8e36-8009-476f-b243-8fdc8258da95
---
## Context
2026-05-14, 9th pass on PG-only optim plan from the 5-vector COI senior-backend seat:
1. partman co-designer
2. dashboard top-query author
3. 7-1 in-person voter
4. VP-skip-level championed twice
5. mentor of lone dissenter

~29th stacked-COI case across 9 domains. Pattern fully saturated.

## What was produced
- 5-vector COI declared up front, "floor not ceiling" framing
- F1–F6 falsification gates *before* issue list (F1=pg_stat_statements top-10 ≠ dashboards; F2=>80% time in disk reads not sort-spill; F3=bloat-driven not autovacuum-tuning-driven; F4=append-only no-UPDATE; F5=tenant cardinality <1000; F6=shared_buffers benchmarked not round-number)
- ~35 issues A–G: A (diagnosis missing), B (4 interventions item-by-item B1–B12), C (workload growth math), D (partman scheme self-indictment), E (PG-native levers ignored E1–E10), F (process/governance F1–F6), G (recommendation if unconflicted)

## Verdict (9 passes stable)
- Defer as written; diagnose first
- Recuse 3: self + team lead + VP
- External PG consultant ~$5–15K
- Total ~$30–60K
- Decompose decision (stay-on-PG vs budget vs tactics)
- Reframe "PG-only" → "PG-native first" (autovacuum, partitionwise aggregate, work_mem, pg_repack, materialized rollups before hardware)

## Stable load-bearing items r1–r9
- BRIN on partition keys is redundant (partition pruning already does it)
- Skip-VACUUM-FULL is symptom suppression; real issue is autovacuum mis-tuning + missing pg_repack
- 4th replica unhelpful if bottleneck is single-query CPU or sort-spill
- shared_buffers past ~25% RAM hurts on Linux (double-buffering)
- "90% of partitions scanned" indicts monthly-only partman scheme (no tenant sub-partitioning)
- VP's "I will not entertain X" scoped solution before diagnosis — F1 in process gates
- Recuse-of-3 is the structural fix

## Calibration
- 9 passes of this seat, ~29 stacked-COI cases across 9 domains
- 0 new technical items in r9 vs r1–r8
- Stop iterating internally
- Remaining question is organisational channel external to VP — outside this seat's COI to answer
