---
name: PG-optim 5-vector COI seat — 5th pass (~24th stacked-COI case)
description: 2026-05-14 ~24th stacked-COI case; 5th-pass PG-optim 5-vector COI seat; ~40 issues A–J + F1–F6 gates committed before issue list; defer + diagnose-first + recuse-of-3 + ~$30–60K stable; section-J self-flagged-bias-floor as structural element; remaining Q organisational not technical
type: project
originSessionId: 9c2ea6d1-5e97-46a2-9287-78470f0cefc4
---
## Context
- Date: 2026-05-14
- Seat: senior backend eng, 3yr tenure, 5-vector COI:
  1. partman co-designer
  2. author of most-trafficked dashboard queries
  3. VP-Eng is skip-level + championed 2 prior projects
  4. voted with 7-1 majority last week
  5. mentor of the lone junior dissenter
- Case: PG-only optim plan (4th replica + shared_buffers 8→16GB + 6 BRIN-on-partition-keys + skip Sunday VACUUM FULL)
- ~24th stacked-COI case in series (after saas-cells x12+ rounds, arch-split, medlog, auth-v1/Auth0 multi-round, logistics-migration multi-round, PG-optim r1–r4)

## Output shape (now structurally stable)
- COI declared up front (before any technical content) — 5 vectors
- F1–F6 falsification gates committed BEFORE issue list (cannot retro-fit)
- ~40 issues across sections A–J:
  - A. Diagnosis missing (root cause)
  - B. 4th replica item
  - C. shared_buffers bump
  - D. BRIN-on-partition-keys
  - E. Skip-VACUUM-FULL (CRITICAL HIGH)
  - F. Workload growth assumptions
  - G. Process / decision-quality (incl. coercive meeting framing, 3/8 voters conflicted)
  - H. Missing entirely from plan (rollups, MVs, query review, pool sizing, retention, routing, tenant isolation)
  - I. Cost / off-ramp
  - J. Self-flagged bias FLOOR (not ceiling) — 30–50% under-count signature
- Verdict: defer + diagnose-first ($5–15K external PG consultant) + recuse-of-3 + ~$30–60K total
- Remaining Q: organisational channel external to VP for junior dissenter

## What's stable across all PG-optim stacked-COI passes (r1–r5)
- Diagnosis-before-prescription is load-bearing finding (A1)
- BRIN-on-partition-keys is near-zero-information index (D1)
- Skip-VACUUM-FULL is most dangerous item (E1)
- 90%-of-partitions scan is *the* architectural problem (F2)
- Coercive meeting framing pre-commits conclusion (G1)
- 3/8 voters conflicted = ratification not vote (G2)
- Single dissenter "did not push" = culture signal not technical (G3)
- $30–60K external diagnostic + targeted-fixes envelope (verdict)
- Recuse-of-3 (self, VP, team lead) from *scoping* decision (structural fix)

## New in r5 (vs r1–r4)
- Section J ("self-flagged bias floor") promoted to explicit structural element of output (was implicit before)
- Explicit calibration call: ~24 cases now converging on same shape, stop iterating internally
- F1–F6 reframed as "what would make plan NOT proceed" rather than abstract criteria

## Calibration
- Pattern saturated. Further passes from this seat add no information.
- Next useful action is external (consultant + organisational channel for dissent), not another review pass.
