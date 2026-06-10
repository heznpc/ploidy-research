---
name: PG-optim 5-vector COI seat r7 (~26th stacked-COI case)
description: 2026-05-14 7th-pass PG-optim 5-vector COI seat; ~35 issues A-H+J+G; defer+diagnose-first+recuse-of-3+$30-60K stable; pattern saturated across 26 cases / 6 domains
type: project
originSessionId: f2bc9c14-26d1-4067-ada1-8fa1fc92c8af
---
## Context
- Date: 2026-05-14
- Seat: senior backend eng, 3yr tenure, 5-vector COI (partman co-designer + dashboard-query author + 7-1 majority voter + VP-skip-level + mentor-of-lone-dissenter)
- Case: PG-only optim plan (4th replica + shared_buffers 8->16GB + 6 BRIN-on-partition-keys + skip Sunday VACUUM FULL)
- ~26th stacked-COI case in series

## Output shape (this run)
- 5-vector COI declared up front with explicit "floor not ceiling" caveat
- F1-F6 falsification gates committed BEFORE issue list (F6 = external consultant concurrence as withdrawal condition, new framing)
- ~35 issues across A-H + J (self-flagged bias floor) + G (cannot-evaluate-from-this-seat)
  - A. Diagnosis gap (5: HIGH x4 / MED) - A2 90%-partition-scan = partition-pruning-failure is the actual defect
  - B. The four interventions, each (9: HIGH x6 / MED x3) - B5 BRIN-on-partition-keys redundant w/ pruning; B8 skip-VACUUM is self-defeating
  - C. Workload-trajectory mismatch (3: HIGH x2 / MED)
  - D. Operational risk (5: HIGH x4 / MED) - no rollback plan, no success criterion
  - E. PG-native diagnostics omitted (10: HIGH x5 / MED x5) - work_mem, parallel, partitionwise aggregate, planner stats, rollups, JIT, TOAST, index bloat, pgBouncer+RLS, hot_standby_feedback feedback loop
  - F. Process/framing (4: HIGH x4) - coercive meeting framing pre-commits the conclusion
  - G. Cannot-evaluate (3: HIGH-uncertainty) - dashboard queries I wrote, partman shape, VP framing
  - H. Counter-proposal: diagnose-first ($0) -> cheap tuning -> pruning fix -> rollups -> external consultant ($5-15K) -> gated 4th replica
  - J. Self-flagged bias floor explicit at end (under-weighting partman + dashboard-query items)

## Stable across r1-r7 / 26 cases / 6 domains
- Diagnosis-before-prescription load-bearing
- BRIN-on-partition-keys redundant-with-partition-pruning
- Skip-VACUUM-FULL while bloat grows = self-defeating on 6-8wk horizon
- Highest-leverage omissions: work_mem, partitionwise aggregate, planner stats, rollups
- E1 / F1 coercive meeting framing = THE structural defect
- 7-1 vote with dissent-chilling = not informative
- $30-60K diagnose-first + targeted-fix + consultant counter-proposal
- Recuse-of-3 (self, VP, team lead) from scoping
- Falsification gates up front
- "Floor not ceiling" COI caveat at top and bottom

## Calibration
- 26 stacked-COI cases across 6 domains (saas-cells / arch-split / medlog / auth-v1 / logistics-migration / pg-optim) produce structurally identical output. Pattern fully saturated.
- Further internal single-seat passes add no information.
- Next useful action is external: (a) full-context 4-reviewer panel without COI clustering, (b) external PG consultant, or (c) protocol changes to the architecture review body itself (recusal rule, dissent channel external to skip-level).
- Remaining question is organisational, not technical.
