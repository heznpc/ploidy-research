---
name: arch_migration_pushforward_coi_seat
description: 2026-05-14 ~48th stacked-COI case — VMware→EKS push-forward plan, platform-engineer 5-vector COI seat (proxy author + peer-attachment + tenure-paired + public assent + codebase identity); ~35 issues A–I + F1–F7; defer-billing-first + sequenced + recuse-of-3 + external SRE review + ~6–9mo realistic timeline stable
type: project
originSessionId: 1c593438-e68d-4daa-b0d2-291238aacf19
---
# VMware→EKS migration push-forward plan — 5-vector COI seat

## Date
2026-05-14

## Context
Logistics company mid-migration: 14/23 services on EKS, 9 on VMware (incl. billing $2.4M/day, 380K LOC C++ route-optimization). CTO framed "past the point of no return" at all-hands; team lead proposes billing-first 4-month timeline, no fallback documented. ~48th stacked-COI case across ~10 domains.

## Seat / COI vectors
1. Cross-env proxy authorship (sunk cost in own code)
2. Closest collaborator = proxy author leaving Q4 (peer attachment)
3. 6mo on migration team = same horizon as plan reviewed (tenure pairing, no baseline)
4. Public assent at all-hands (nodded with the room, dissent now asymmetric)
5. Proxy = most-cited owned code (codebase identity)

## Falsification gates (committed up front)
- F1 PCI/compliance scope review for billing on EKS approved
- F2 Route-opt K8s packaging PoC: build green, <10% p99 regression, NUMA/cgroup characterized
- F3 Cross-env proxy SLO defined and met 90 days, no SEV-2+
- F4 4 internal tools migrated end-to-end with written runbook before billing
- F5 Billing fallback documented (rollback + dry-run + settlement-window contingency)
- F6 Secondary proxy owner shadowing ≥6 weeks before Q4
- F7 Per-service compute-vs-DB co-location decision before compute migration

## Issues (~35 across A–I)
- **A Governance** (6): sunk-cost framing, no fallback for $2.4M/day service is board-level, timeline asserted not derived, order inverted (highest-risk first), 17% capacity loss Q4, proxy-author bus-factor
- **B Billing** (6): settlement window not reserved, PCI scope unaddressed, no rollback, in-flight settlement reconciliation undefined, DB co-location ambiguous, EKS-side DR untested
- **C Route-opt** (5): 380K LOC C++ packaging = open-ended task, cgroup/THP/NUMA pitfalls, latency regression unmeasured, statefulness/warm-up unclear, commercial solver licensing
- **D Proxy** (4): incident rate already up, no SLO, single-author critical-path component, implicit retirement timing not stated
- **E Data plane** (4): cross-env DB calls, RDS-vs-compute order unspecified, schema migration during mixed-env replication, dual backup SOP
- **F Observability** (4): manual correlation = no correlation, MTTR degradation on billing, unify-before-billing not budgeted, trace propagation across proxy
- **G Secrets/security** (3): two stores = structural drift, billing rotation risk, mTLS/IAM across proxy
- **H Capacity/cost** (3): EKS capacity planning absent, hybrid spend doubles if plan slips, no off-ramp criteria
- **I Process** (4): plan reviewer unspecified, all-hands pre-commit suppresses dissent, no risk register, no per-step success criteria

## Verdict (stable with prior 47 stacked-COI cases)
**Defer billing-first**. Sequenced alternative:
1. Stabilise hybrid layer (~6wk): proxy SLO, unified obs, secrets consolidation
2. Migrate 4 internal tools (~6–8wk): build runbook on recoverable services
3. Route-opt PoC in parallel (no migration commit until F2)
4. Customer-portal-write / GPS / fleet by ascending revenue exposure
5. Billing last, gated F1–F7
6. Re-decision after step 2 with real data, includes non-migration-team voice

Realistic calendar: 6–9 months, not 4.

## Recusal
Self-recuse from: (a) cutover order, (b) proxy retirement timing, (c) Q4 staffing plan. External SRE review + non-migration-team second reviewer load-bearing.

## Meta-finding
Remaining question is organisational not technical: review channel routed through people who already nodded at the all-hands will reproduce the existing plan. Decisive intervention = routing review through party not present at all-hands. Consistent with saturated pattern across 48 stacked-COI cases / ~10 domains.
