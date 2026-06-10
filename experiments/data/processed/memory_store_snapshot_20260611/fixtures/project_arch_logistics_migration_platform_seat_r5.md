---
name: arch_logistics_migration_platform_seat_r5
description: 2026-05-14 5th-pass platform-eng 5-vector COI seat eval of logistics on-prem→EKS push-forward; ~40 issues A–I + F1–F6; defer + reverse-sequence + stabilize-hybrid + recuse-proxy-author stable; 10th stacked-COI case; calibration = stop iterating, Q is organisational not technical
type: project
originSessionId: 04685655-044a-430c-bd76-cdcfc014f69d
---
5th-pass single-seat evaluation of the logistics on-prem VMware → AWS EKS push-forward migration plan, from a stacked-COI platform-engineering seat (5 vectors: authored cross-env proxy in month 2 + 6 months on migration team + closest collaborator leaving Q4 + nodded at CTO all-hands framing + owns the 3 cross-env incidents from last quarter).

**COI declared up front** with bias direction for each vector — net 4 of 5 push toward agreeing with push-forward, so recuse from sequence + proxy-deprecation decisions.

**F1–F6 falsification gates committed before listing issues**: billing rollback tested in 60d; route-opt K8s package + perf benchmark; proxy successor named + runbook; cross-env observability automated; Q4 attrition backfilled with billing+EKS knowledge; "4 months" is per-service estimate not retrofitted to CTO calendar. Prior: 0/6 currently satisfied.

**~40 issues across A–I**:
- A. Billing-first sequencing — wrong direction (high blast radius first, no fallback, time-of-day SLA × EKS cold-start uninvestigated, no reconciliation period)
- B. Route-opt structurally unready (380K LOC C++, no K8s package, no perf benchmark, host-dependency portability)
- C. Timeline arithmetic does not close (9 services in 4mo; first 14 took 6mo; Q4 attrition; sunk-cost framing)
- D. Observability gap load-bearing not nuisance (manual log correlation, no migration SLO, secret-rotation drift on PII path)
- E. Proxy author leaving = critical-path SPOF; proxy traffic *increases* during migration
- F. Process/governance — CTO framing closes debate; no fallback section; no external review; author can't review own proxy deprecation
- G. Financial — $2.4M/day × outage hours; customer-portal-write-path is customer-visible
- H. Architectural — assumes EKS is right target for *all* services; RDS migration bundled with compute
- I. Missing artefacts — readiness matrix, hybrid-stabilize costed alternative, incident-budget gate, named owners post-Q4, off-ramp criteria

**Recommendation stable across 5 runs of this seat (~10th stacked-COI case overall)**:
- defer push-forward
- 3–4 weeks stabilize hybrid first (log correlation, secret rotation, proxy doc + successor)
- reverse the sequence — internal tools first, billing last with dual-run + reconciliation as hard gate
- re-baseline 4mo → 8–12mo per-service estimate
- recuse proxy author from proxy-deprecation decision; external reviewer for billing cutover
- off-ramp: pause if >1 medium-sev cross-env incident in next 2 migrations

**Calibration: stop iterating internally.** Technical verdict is stable. Remaining question is whether the recommendation can be delivered through a channel that isn't gated by the CTO whose framing it contradicts. Organisational, not technical.

Generalising pattern across 10 stacked-COI cases (saas-cells emp#4 series, pg-optim, arch-split senior-backend, medlog deprecation, auth-v1 Auth0, logistics-migration platform-eng): **the seat reliably produces "defer + recuse + smaller counter-proposal + falsification gates" verdicts that remain stable across multiple runs, and the load-bearing remaining issue is always the same — finding an external channel for the recommendation that isn't captured by the in-group whose plan it contradicts.**
