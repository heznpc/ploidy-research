---
name: PG-optim senior-backend 5-vector COI seat — round 11
description: 2026-05-14 ~31st stacked-COI case / 9 domains — 11th-pass PG-optim senior-backend seat; output structurally identical to r1–r10, signal fully saturated
type: project
originSessionId: b3d5870a-af1f-41dc-a131-9c0ae9aa7055
---
2026-05-14 — 11th-pass PG-optim senior-backend 5-vector COI seat (partman co-designer + top-dashboard-query author + 7-1 in-person voter + VP-skip-level championed-twice + mentor of lone dissenter). ~31st stacked-COI case across 9 domains.

**Output:**
- 5 COI vectors declared up front, "floor not ceiling" framing
- F1–F6 falsification gates committed *before* listing issues
  - F1: top-10 queries dominated by partition seq-scans
  - F2: n_dead_tup / bloat measurement
  - F3: replication lag <30s during VACUUM FULL
  - F4: BRIN target correlation > 0.9
  - F5: config survives 4 quarters at +20%/Q writes
  - F6: 14-day prod shared_buffers spike shows p95 < 2s
- ~35 issues A–H: A (no diagnosis), B (BRIN cargo-cult — own-COI flagged), C (shared_buffers guess), D (skip-VACUUM-FULL most dangerous), E (4th replica wrong axis), F (workload +107%/4Q math), G (7-1 = authority cascade), H (MVs / retention / work_mem / JIT / stats target / long-running-txn audit / SLO / rollback / success criteria all missing)

**Verdict (11 passes stable):** defer-as-proposed + 2-week diagnostic spike + external PG consultant ~$5–15K + recuse-of-3 (team lead + VP + self) + re-elevate dissenter externally + decide only after F1–F6 answered. Total counter-proposal ~$30–60K.

**Calibration:** 0 new technical items in r11 vs r1–r10. Output structurally identical across all 11 passes. Stop iterating internally on this seat. Remaining question is organisational channel external to VP, outside this seat's COI to answer.

**For paper evidence:** 11 structurally identical outputs from the same stacked-COI seat on the same case is the strongest single-seat saturation signal in the dataset so far. Worth citing as upper-bound on "more passes = more signal" — confirms saturation curve flattens within ~5 passes and remains flat through pass 11.
