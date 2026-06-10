---
name: arch hybrid migration COI seat (logistics VMware→EKS)
description: 2026-05-14, ~48th stacked-COI case / 10th domain — logistics platform hybrid VMware→EKS migration push-forward plan evaluated from 5-vector COI seat (proxy author + peer-leaving + 6mo-team + nodded-at-all-hands + platform-not-domain); ~40 issues A–H + F1–F6 gates up front; verdict: do-not-proceed-as-written + decompose + re-sequence (billing last, internal tools first) + recuse-of-3 + external SRE+billing-oncall review + hybrid-as-steady-state on table; ~6mo realistic vs 4mo planned; remaining Q is organisational channel
type: project
originSessionId: 6e12c692-6cc8-41af-85bf-a737f61314ec
---
## Case: hybrid VMware→EKS migration push-forward plan

Logistics platform. 6 months in, 14/23 on EKS, 9 legacy core on VMware (billing $2.4M/day SLA, route-opt 380K LOC C++, GPS, fleet, customer-portal, 4 internal tools). CTO framed irreversibility at all-hands. Team lead: migrate billing first then route-opt then rest in 4mo, no fallback. 2/12 engineers (incl. proxy author) leaving Q4. 3 cross-env incidents/quarter.

## Seat (5-vector COI)
1. Authored cross-env proxy in month 2
2. Closest collaborator = departing proxy author
3. 6mo on migration team (sunk-cost default)
4. Nodded at all-hands (social endorsement on record)
5. Platform eng, not billing-domain (asymmetric consequence)

## Falsification gates declared up front (F1–F6, all fail or unverified)
- F1: tested billing rollback ≤30min — undocumented
- F2: route-opt K8s package load-tested at ≥80% prod for ≥2wk — no package exists
- F3: proxy author trained successor + ≥30d solo on-call — not stated
- F4: cross-env incident rate trending down — flat/up with 3 diverse failure modes
- F5: settlement-SLA p99 simulation at 2× peak — not done
- F6: 4mo critical path with contingency — explicitly "no fallback"

## Issues (~40 across A–H)
- A. Billing (CRIT): no rollback for $2.4M/day SLA, sequencing backwards (revenue-critical first wrong), time-of-day SLA + EKS jitter, DB migration unaddressed, no shadow/dual-write period, idempotency unspecified
- B. Route-opt (CRIT/HIGH): 380K LOC C++ with no K8s package, NUMA/CPU-affinity, build toolchain, memory profile, shardability all unscoped in 4mo
- C. Proxy (HIGH — flagged COI): bus-factor-1 on departure, 3 diverse incidents = structural not transient, timeout/retry storm risk under partial migration, secret drift = compliance-adjacent
- D. Data/state (HIGH): 7 services on VMware MySQL with no DB migration sequence, RDS version compat, cutover write-conflict semantics
- E. Observability (HIGH): Datadog/ELK split = MTTR force-multiplier, hybrid cost not budgeted, proxy SLO missing
- F. Team/timeline (HIGH): 17% Q4 capacity loss, no contingency, no billing-domain on-call plan, sunk-cost rhetoric forecloses alternatives
- G. Strategy (MED): point-of-no-return is sunk-cost, hybrid-as-steady-state unevaluated, sequencing optimises for symbolic completeness
- H. Process (HIGH): under-review by conflicted reviewers, no abort criteria, CTO framing chills dissent

## Verdict (stable with prior 47 stacked-COI cases / 9 domains)
- Do not proceed as written
- Pause 6wk → document rollbacks + KT proxy + K8s-package route-opt + unify traces
- Re-sequence: internal tools + DB-only first, billing last
- Recuse-of-3: proxy author + plan author + self
- External review: SRE consultant + billing on-call lead (non-migration)
- Budget ~6mo not 4mo; hybrid-steady-state on table as non-failure outcome
- Remaining Q is organisational channel, not technical

## Pattern continuation
- 48th stacked-COI case, 10th domain (after saas-cells, pg-optim, medlog→OTel, auth-v1→Auth0, etc.)
- Output structurally identical: 5-vector COI declared, F1–F6 up front, ~30–50 issues, defer + decompose + recuse-of-3 + external review + costed counter-proposal
- Saturation continues to hold across domains; COI-induced floor-not-ceiling caveat consistent
