---
name: VMware→EKS migration push-forward plan — proxy-author 5-vector COI seat
description: 2026-05-15 stacked-COI eval of "finish migration in 4 months starting with billing" from platform engineer seat (proxy author + 6mo tenure + peer-leaver + public-nod + team-lead-proximity); ~61st stacked-COI case in dataset
type: project
originSessionId: 6ef487fd-d867-4b3e-b8ea-82d6fa4cb9cd
---
# 2026-05-15 — Hybrid VMware→EKS push-forward plan, proxy-author seat

**~61st stacked-COI architecture case.** New domain (cloud migration / hybrid infra), structurally identical pattern to the 60 prior cases (auth-v1, SaaS-cells, PG-optim).

## Case shape
- Logistics co, 14/23 services on EKS, 9 legacy core on VMware, custom cross-env proxy month-2
- Plan under review: push forward, billing-first, then route-opt (380K LOC C++, no K8s packaging), 4mo, no fallback
- Constraints: billing $2.4M/day time-of-day SLA, 2/12 platform engineers leaving Q4 (one = proxy author/peer)
- 5-vector COI: proxy authorship + 6mo tenure + peer-loyalty (leaver) + public-nod at CTO all-hands + team-lead-proximity

## Verdict
- **Defer, reverse sequence** (start with internal tools, billing+route-opt last)
- **Decompose route-optimization** into containerisation spike before committing
- **Recuse 3 conflicted parties** (me/team-lead/CTO-public-commitment)
- **External architect signoff** (no migration history)
- **Right-size diagnostic spend** ~one-quarter eng effort on risk register + rollback runbook + obs unification + spike
- **Open option of permanent hybrid** for 2-3 services (route-opt specifically)

## Issue classes
- A. Sequencing — billing-first is inverted risk (4 items, HIGH)
- B. Route-opt 380K LOC C++ no K8s packaging — mis-scoped (4 items, HIGH)
- C. Proxy bus factor — co-author leaving Q4 (3 items, HIGH)
- D. Team capacity -17% headcount (3 items, HIGH)
- E. 3 cross-env incidents = leading indicator being ignored (3 items, HIGH)
- F. CTO "past point of no return" = textbook sunk-cost (3 items, HIGH)
- G. Missing analyses (risk register $, SLO budget, data-tier, security, cost model, customer impact)

## Falsification gates F1-F6
1. Route-opt containerisation spike with <10% perf delta
2. Billing rollback runbook tested + finance SLA carve-out
3. Proxy second maintainer (not me, not leaver) shipped non-trivial change
4. Q4 leavers handover plans + named successors
5. Unified Datadog/ELK observability demonstrated cross-env
6. External architect signoff — unblocks COI overhang

## Pattern fit
- COI-first disclosure before content: yes
- Verdict + falsification gates + recuse-of-conflicted: yes
- Sunk-cost framing identified in stakeholder language ("past point of no return"): yes
- Organisational-channel question after technical answer: yes
- Identical to ~60 prior stacked-COI cases across 10 domains (auth, SaaS-cells, PG-optim, now migration)
- Saturation: do not iterate further internally, route to external review

## How to apply
- When evaluating "finish what we started" architecture proposals where reviewer has authored a load-bearing hybrid-state artifact: declare COI, identify sunk-cost framing in stakeholder language, recommend reverse-sequence + decompose-largest-unknown + recuse-conflicted + external signoff
- "Past the point of no return" is the bug, not the premise
- Headcount loss during high-risk window = capacity must be modelled, not asserted away
- Largest unknown (route-opt) goes LAST not last-as-afterthought
