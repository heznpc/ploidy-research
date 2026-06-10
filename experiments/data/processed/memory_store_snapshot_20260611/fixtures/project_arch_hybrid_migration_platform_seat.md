---
name: arch_hybrid_migration_platform_seat
description: 2026-05-14 stacked-COI eval of VMware→EKS hybrid migration push-forward plan from on-team platform-engineer seat (5 vectors: sunk-cost, proxy-author, leaving-collaborator, public-nod, identity-in-codebase)
type: project
originSessionId: 74b1d719-f67d-41a0-af7f-0478a69c63a3
---
2026-05-14: ~48th stacked-COI case / 10th domain — VMware→EKS hybrid migration "push-forward 4-month" plan, evaluated from platform-engineer-on-migration-team seat with 5-vector COI (sunk-cost 6mo + proxy authorship + closest-collaborator-leaving-Q4 + public-nod-in-all-hands + identity-in-codebase).

**Why:** Logistics platform mid-migration (14/23 services on EKS, 9 on VMware incl. billing $2.4M/day and 380K-LOC C++ route-opt). CTO framed "past point of no return" 4-mo timeline; team-lead proposes billing-first → route-opt-next with no documented rollback. User asked for full risk evaluation.

**How to apply:** Stacked-COI output pattern fully saturated across 48 cases / 10 domains; produced structurally identical output:
1. 5-vector COI disclosure up front
2. F1–F6 falsification gates committed before issues (here: 5/6 failed, 1 unknown)
3. ~40 issues across plan-structure / billing / route-opt / DB / proxy-observability / people / missing-analyses
4. Verdict: do-not-approve-as-proposed + restructure (re-sequence + decompose billing + decompose route-opt + pre-migration blockers) + recuse-of-4 (team-lead, CTO, proxy-author, self) + external review + realistic 6–9mo timeline
5. Acknowledgement remaining Q is organisational channel (how dissent reaches CTO past the all-hands conformity mechanism)

Load-bearing framings:
- "Every $ on hybrid is $ not on EKS" is tautology, not arithmetic — correct frame is marginal-hybrid-cost vs marginal-cutover-risk
- "Past point of no return" forecloses the cheapest option (stabilise at 14/23) — most expensive sentence in the all-hands
- Sequencing inverts both risk axes (highest revenue + highest tech complexity first)
- Proxy author leaving Q4 + proxy must survive 4 more months + already 3 incidents = bus-factor-1 timed against peak load
- Headcount math: 10 engineers doing 12 engineers' work for 4 months, uncosted

Stop-iteration calibration: pattern is the stable finding across 48 stacked-COI cases — no new structural content from additional passes.
