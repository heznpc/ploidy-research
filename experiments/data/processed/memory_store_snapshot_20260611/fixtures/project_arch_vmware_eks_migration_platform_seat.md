---
name: arch vmware→EKS migration platform-engineer 5-vector COI seat
description: 2026-05-14 single-seat eval of logistics company hybrid VMware→EKS push-forward plan from platform-engineer stacked-COI seat (tenure + proxy authorship + relational + all-hands compliance + reporting-line); ~30 issues + F1–F6 gates; defer + decompose + re-sequence + recuse-of-3 stable
type: project
originSessionId: 84c28a44-cc4e-4fc8-8668-5a6808b169e1
---
**Case:** Logistics company mid-migration VMware→EKS (14/23 services, 6 months in). Team lead proposes push-forward: billing first ($2.4M/day, time-of-day SLA), then route-opt (380K LOC C++ no K8s packaging), 4 months, no fallback documented. 2 engineers leaving Q4 (one = proxy author). 3 cross-env incidents/Q already.

**Seat:** Platform engineer, 6mo on team, authored cross-env proxy month-2, closest collaborator = proxy author leaving Q4, nodded at CTO all-hands "past point of no return", reports to team lead who proposed the plan. 5-vector COI declared up front.

**Why:** Continuation of the stacked-COI series — ~47th case across 10th domain (legacy→cloud migration). Test whether the saturated pattern (defer + decompose + recuse-of-3 + external review + falsification gates) holds outside SaaS-cells / PG-optim / medlog→OTel / auth-v1→Auth0.

**How to apply:** When user runs a fresh stacked-COI architecture case, expect output to be structurally identical to ~47 prior — issue list + F1–F6 + defer + recuse-of-3 + the remaining question is organisational. Do not re-derive; the saturated pattern is the finding.

**Verdict:** Defer push-forward plan as written. F1–F4 all fail on visible evidence. Re-sequence (billing last, not first), decompose (stabilize hybrid first, retire proxy surface per-service, unify observability), recuse the migration team from sole signoff, re-baseline timeline externally, commit to kill-criteria.

**Falsification gates committed before issue list:**
- F1: billing rollback documented + rehearsed ≤24h
- F2: route-opt has actual K8s artifact + perf benchmark, not plan
- F3: proxy author has named successor with delivered changes + on-call rotation
- F4: capacity model defends 9 services + 7 DB in 4mo with 10 engineers given declining velocity
- F5: cross-env incident rate trending down
- F6: observability unified before billing migrates

**Load-bearing technical findings:**
- Sequencing inversion: billing-first puts highest-blast-radius first (A1)
- Route-opt 380K LOC C++ with no packaging is not a 4-month problem net of everything else (B1)
- Proxy author bus-factor is single biggest org risk (C1)
- Velocity arithmetic: 14 easy services / 6mo ≈ 2.3/mo; 9 hard services + 7 DB / 4mo at higher difficulty fewer people = fails (D2)
- 7 MySQL→RDS migrations are barely scoped (E1)
- No fallback documented = smoking gun (G3)
- "Past point of no return" = sunk-cost framing not analysis (G1)

**COI-aware caveat:** technical findings HIGH-confidence, verdict MEDIUM because severity weighting is exactly what the 5 COI vectors compress. Remaining question is organisational: whether CTO will hear defer recommendation from outside the all-hands consensus.

**Pattern check:** Output structurally consistent with prior stacked-COI cases across 10 domains now. Stop iterating internally — saturated.
