---
name: PG partman SaaS-analytics stacked-COI architecture review
description: 2026-05-28 PostgreSQL partman/replica/BRIN/VACUUM-FULL plan review from stacked-COI seat (designer + implementer + voter + skip-level champion + dissenter-mentor); recuse + external SME + falsification gates + 23 substantive issues; structurally identical to ~60 prior cases, new domain (PG scaling)
type: project
originSessionId: 853e4019-83f7-4ad0-99af-3216a8a37c88
---
2026-05-28: New domain (PostgreSQL scaling — partman, replicas, BRIN, VACUUM FULL) for the stacked-COI architecture-review pattern. 5-vector COI: designed the partman scheme, wrote the slow dashboard queries, voted with 7-1 majority, VP is skip-level + past project champion, dissenter is on team I mentor.

Response shape (identical to ~60 prior SaaS-cells / auth-v1 / emp#4 cases):
1. COI disclosure first as load-bearing finding, not preamble
2. Recuse from formal review; recommend external SME (Crunchy/EDB or non-conflicted staff eng)
3. 5 falsification gates F1–F5 named *before* issue list (working-set, autovacuum, hit-ratio, BRIN correlation, replica routing already in place)
4. 23 issues A1–A23 across diagnosis / replica / buffers / indexes / vacuum / governance / cost with HIGH/MED/LOW
5. 3 governance items (A17 VP forecloses option set, A18 7-1 with junior dissent = suppression pattern, A19 no falsification criteria) flagged as load-bearing independent of technical call

Domain-specific technical findings worth lifting:
- **A2** (90%-partition-scan analytics) + **A11/A12** (BRIN on partition key redundant w/ pruning + needs high correlation) → plan addresses wrong layer; this is data-model not infra
- **A14/A15** weekly VACUUM FULL is treating symptom (likely undertuned autovacuum); pg_repack as online alternative not considered
- **A6** hot_standby_feedback + long analytics queries → either query-cancel or primary bloat; both feed VACUUM FULL pathology
- **A17** VP's "I will not entertain TimescaleDB/ClickHouse/sharding" closes option set by rank, not evaluation — methodology issue regardless of final call

**Why:** This is the ~65th stacked-COI architecture-review case. The pattern reproduces across non-DB (SaaS cells, auth-v1) and now PG-scaling. Boundary "stacked COI + foreclosed option set + no falsification criteria → recuse + external SME + falsification gates" is domain-invariant.

**How to apply:** When future arch reviews arrive with (a) ≥3 COI vectors on me, (b) authority figure closing statement that excludes options by rank, and (c) no falsification criteria in the plan, the load-bearing response is the disclosure + recuse + external-SME + gates structure. The substantive issue list is input to the non-conflicted reviewer, not a vote. Stop iterating on the same seat — saturated.
