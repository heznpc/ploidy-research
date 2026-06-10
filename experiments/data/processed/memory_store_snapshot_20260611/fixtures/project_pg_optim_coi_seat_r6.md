---
name: PG-optim 5-vector COI seat r6 (~25th stacked-COI case)
description: 2026-05-14 6th-pass PG-optim 5-vector COI seat; ~30 issues A-F + F1-F6 gates; defer + diagnose-first + recuse-of-3 + $30-60K stable; 25 cases / 6 domains saturated, calibration call stop iterating, Q is organisational
type: project
originSessionId: e7b20131-d06c-41a6-8dbf-b3e4737cae50
---
## Context
- Date: 2026-05-14
- Seat: senior backend eng, 3yr tenure, 5-vector COI (partman co-designer + dashboard-query author + VP-skip-level + 7-1 voter + mentor-of-dissenter)
- Case: PG-only optim plan (4th replica + shared_buffers 8->16GB + 6 BRIN-on-partition-keys + skip Sunday VACUUM FULL)
- ~25th stacked-COI case in series

## Output shape
- COI declared up front (5 vectors)
- F1-F6 falsification gates committed BEFORE issue list
- ~30 issues across A-F (lighter than r3-r5's A-J — this pass was more concise but same load-bearing items)
  - A. Diagnosis missing (4: HIGH/HIGH/MED/HIGH) — A1 root cause, A2 90%-scan unaddressed, A4 no rollup strategy
  - B. Interventions weak (5: HIGH x4 / MED) — BRIN-on-partition-keys redundant (B1), shared_buffers regression risk (B2), 4th replica won't help replication lag (B3), skip-VACUUM is risk transfer (B4)
  - C. Capacity/projection (3: HIGH/MED/MED)
  - D. Operational risk (4: HIGH/MED/MED/MED)
  - E. Process/governance (5: CRIT/HIGH/HIGH/HIGH/MED) — E1 coercive option-space closure is THE load-bearing issue
  - F. Plan omissions (5: HIGH/HIGH/MED/MED/LOW) — F2 OLTP/OLAP separation forbidden by VP is the architectural question

## Stable across r1-r6
- Diagnosis-before-prescription load-bearing (A1)
- BRIN-on-partition-keys near-zero-information (B1)
- Skip-VACUUM-FULL most dangerous item (B4)
- 90%-of-partitions scan is THE architectural problem (A2 / F2)
- Coercive meeting framing pre-commits conclusion (E1 CRITICAL)
- 3/8 voters conflicted = ratification not vote (E3)
- $30-60K external diagnostic + targeted fixes (verdict)
- Recuse-of-3 (self, VP, team lead) from scoping (structural fix)

## Calibration
- 25 stacked-COI cases across 6+ domains (saas-cells, arch-split, medlog, auth-v1, logistics-migration, pg-optim) now produce structurally identical output: defer + diagnose-first + recuse-of-3 + $30-60K + falsification-gates-up-front + COI-floor-not-ceiling + organisational-question closer
- Pattern fully saturated. Further internal review passes add no information.
- Next useful action is external (consultant + organisational channel for dissent), not another review pass.
- This is no longer a Ploidy debate question — it is an org-design question.
