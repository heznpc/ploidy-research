---
name: arch logistics migration proxy-author seat
description: 2026-05-14 logistics on-prem→EKS push-forward plan eval from proxy-author + 6mo migration team + departing-peer-collaborator + all-hands-nodder + codebase-identity (5-vector COI) seat; ~30 issues A–H + F1–F6 gates up front; halt-60d + decompose-billing + external-review + recuse-of-3 + re-decide stable; ~48th stacked-COI case / 10th domain
type: project
originSessionId: d8c0c23c-7896-4e40-af55-27faffe66499
---
# Logistics VMware→EKS migration — proxy-author 5-vector COI seat

**Date:** 2026-05-14
**Case #:** ~48th stacked-COI case (10th domain — first logistics/infra-migration domain)

## Seat (5-vector COI)
1. Proxy author (month 2) — my code is the bridge being deprecated; sunk cost
2. 6-month migration team member — sunk cost in the path
3. Departing peer is closest collaborator — "finish before they go" affective weight
4. Nodded at all-hands — public alignment with CTO framing, social cost to dissent
5. Codebase identity — career narrative = "migration platform engineer"

## Proposal under review
- CTO framing: "past point of no return, finish in 4 months, feel the pain"
- Team lead: billing-first ($2.4M/day, time-of-day SLA) → route-opt (380K LOC C++, no K8s pkg) → rest
- 9 services on VMware, 14 on EKS, custom cross-env proxy, 2 engineers leaving Q4 (incl. proxy author), no fallback plan documented, 3 cross-env incidents last quarter

## Falsification gates (committed up front)
- **F1** route-opt packaging demonstrable on staging EKS in ≤8 weeks 1 eng before billing cutover
- **F2** billing rollback drilled in pre-prod with synthetic load, ≤30min restore of time-of-day SLA
- **F3** proxy-author handover complete (runbooks + 2 trained backups + 1 real incident) before Q4 departure
- **F4** hybrid-maintenance cost line costed separately, reviewed outside migration team
- **F5** "halt 6mo, re-decide" option costed with same rigor and explicitly rejected on written criteria
- **F6** every next-4mo service has per-service written rollback (not "we'll feel the pain")

## ~30 issues across A–H
- **A** sequencing: billing-first wrong (max blast radius for rehearsal), "then the rest" no dep graph, 4mo = ~13d/service implausible, no off-ramp
- **B** billing: time-of-day SLA tolerance, exactly-once/reconciliation unstated, DB cutover concurrency with compute, cron→CronJob semantics
- **C** route-opt 380K C++: 8–16wk packaging realistic, PDB/drain/spot-eviction for stateful solver, CI/build cache, NUMA/hugepages regression
- **D** proxy + author: bus-factor=1 during highest-risk period, 3 incidents last qtr = steady-state failure mode, secret-rotation drift foreshadows cutover Sev1, **self-recuse from assessing my own proxy**
- **E** DB: 7 MySQL + 2 RDS hybrid, no CDC strategy stated, no hybrid backup/restore drill, cross-env join latency
- **F** observability: Datadog/ELK split + manual correlation = SRE bottleneck at 3AM, no unified tracing across proxy
- **G** team: 2/12 leaving Q4, route-opt C++ expertise possibly walking, burnout death spiral
- **H** governance (most important): "past point of no return" = sunk cost not analysis; "every $ on hybrid = $ not on EKS" false dichotomy; CTO framing anchors dissent; team-lead + CTO + migration-team all conflicted; **dissent channel missing**; falsification gates not committed in writing; "no fallback plan" alone is stop-ship

## Verdict (stable)
- **Do not proceed as written**
- Counter-proposal:
  1. Halt 60d, stabilize hybrid, fix 3 known incident classes, complete proxy-author handover
  2. Decompose billing (compute/DB/cron separately rollback-able); rehearse on internal tool first, not billing
  3. External reviewer outside migration team, applies F1–F6
  4. **Recuse-of-3**: proxy author (me), team lead, departing peer from billing go/no-go
  5. Re-decide day 60 with packaging spike + billing rollback drill + F1–F6 evidence

## Pattern observation
- 10th domain (saas-cells, arch-split, pg-optim, medlog→OTel, auth-v1/Auth0, + others) showing identical structural verdict: defer/decompose/sequence + recuse-of-3 + external review + falsification gates + dollar-bounded counter
- The technical specifics differ; the **governance verdict does not**
- Suggests the COI pattern is decision-architecture-shaped, not domain-shaped
- Remaining question across all 10 domains is the same: **organisational channel for surfacing the recuse-of-3 finding to a body that can act on it**, since the conflicted parties are typically the ones who would receive the recommendation
