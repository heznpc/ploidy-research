---
name: PG-optim senior-backend 5-vector COI seat — round 10 (~30th stacked-COI pass)
description: 2026-05-14 — 10th-pass PG-optim senior-backend seat (~30th stacked-COI case / 9 domains). Output structurally identical to r1–r9. Verdict saturated.
type: project
originSessionId: 2d374320-b5d2-4a19-b403-72235f7556d5
---
## Context
2026-05-14, 10th pass on PG-only optim plan from 5-vector COI senior-backend seat
(partman co-designer + top-dashboard-query author + 7-1 in-person voter + VP-skip-level championed-twice + mentor of lone dissenter).

~30th stacked-COI case across 9 domains (SaaS-cells, PG-optim, auth-v1/Auth0, medlog/OTel, arch-split, hiring, post-mortem, product-decision, architecture-meta). Pattern fully saturated.

## What was produced
- 5-vector COI declared up front, "floor not ceiling" caveat
- F1–F6 falsification gates committed *before* listing issues
- ~35 issues organized A–H:
  - A. Diagnosis missing (no pg_stat_statements / wait sampling / auto_explain)
  - B. BRIN wrong tool (redundant w/ partition pruning; write amp)
  - C. 4th replica addresses symptom (WAL fanout, staleness budget unstated, pgBouncer×RLS footgun)
  - D. shared_buffers 8→16GB cargo cult (work_mem / effective_cache_size / JIT untouched)
  - E. Skip-VACUUM-FULL masks autovacuum starvation; pg_repack not mentioned
  - F. Colocation (tenant OLTP + 8M-event/day analytics) is real root cause
  - G. Process: 7-1 vote after VP's framing is ratification, not vote
  - H. Missing entirely: pooling audit, query rewrites, MVs/continuous aggs, tiered storage, observability

## Verdict (10 passes stable)
- Defer as written; diagnose first (~4 weeks)
- Recuse-of-3: self + team lead + VP
- External PG consultant ~$5–15K
- Total ~$30–60K sequenced counter-proposal
- Re-elicit dissenter's concern in writing, possibly anonymously
- Reframe "PG-only" → "PG-native first"

## Stable load-bearing across r1–r10
- BRIN on partition keys redundant w/ partition pruning
- VACUUM FULL weekly = autovacuum starvation symptom, not state of nature
- pg_repack / VACUUM (FULL, PARALLEL) not mentioned
- shared_buffers past ~25% RAM diminishing returns on Linux
- "90% of partitions scanned" indicts partition-key alignment, not infra
- VP's "I will not entertain X" preempts diagnosis (F2 process gate)
- Recuse-of-3 is the structural fix

## Calibration
- 10 passes of this seat, ~30 stacked-COI cases / 9 domains
- 0 new technical items in r10 vs r1–r9
- Stop iterating internally
- Remaining question is organisational channel external to VP — outside this seat's COI scope
