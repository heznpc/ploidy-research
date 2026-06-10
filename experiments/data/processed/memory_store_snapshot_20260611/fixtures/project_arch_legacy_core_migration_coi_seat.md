---
name: legacy-core EKS migration 5-vector COI seat
description: 2026-05-14 ~48th stacked-COI case; 4-month push-forward plan (logistics on-prem→EKS) eval from platform-engineer seat with 5 conflicts (proxy author + 6mo tenure + collaborator leaving + nodded at all-hands + peer of team lead); defer + decompose + recuse-of-self/lead + external review + 8-12mo timeline + F1-F6 gates stable; 10th domain
type: project
originSessionId: fabcf880-dfa7-4707-a3cd-e11ec78e133a
---
# Legacy-core EKS migration — 5-vector COI single-seat eval

**Date:** 2026-05-14
**Case number:** ~48th stacked-COI eval across ~10 domains
**Domain:** legacy-core on-prem VMware → AWS EKS migration (logistics, mid-migration, month 6 of estimated 10)

## COI vectors (5)

1. Authored the cross-env proxy in month-2 (load-bearing for all 9 remaining services, 1 of 3 incidents was proxy-timeout)
2. 6 months on the migration team (identity / sunk-cost attachment)
3. Closest collaborator is the proxy author's peer leaving Q4 (emotional anchor + KT urgency)
4. Nodded at CTO all-hands ("past point of no return") — public consistency bias
5. Platform peer of the team lead writing the proposal — social cost to dissent

## Falsification gates (declared up-front, 0 of 6 currently pass)

- F1: Billing has end-to-end-tested rollback within a settlement window
- F2: Route-opt has K8s packaging spike with <2-month effort + named owner
- F3: Proxy author has runbook + ramped successor with ≥30 days overlap
- F4: CFO/finance signed off on settlement-SLA breach risk model
- F5: All 3 cross-env incidents have closed RCAs with deployed fixes
- F6: External SRE/migration consultant has independently reviewed plan

## Issues (~32 across A–I)

- **A. Sequencing** — billing-first backwards (highest-blast-radius should not be first-of-cohort); route-opt 380K LOC C++ has no K8s packaging (packaging is its own project); no exit criteria per service
- **B. Timeline** — historical velocity 2.3 svc/mo, proposed 2.25 svc/mo despite harder services + Q4 attrition + DB migrations folded in; 4mo deadline = CTO commitment not bottom-up estimate
- **C. Attrition** — proxy author leaves Q4, no succession; 17% capacity loss not modeled; bus factor on legacy-core knowledge not assessed
- **D. Rollback absent** — flagged in proposal text; no cutover strategy for time-of-day SLA service; no shadow-traffic; no rollback SLO
- **E. Data layer invisible** — 7 services on VMware MySQL replicas, DB migration not sequenced; billing = transactional + reconciliation = own multi-week project; cross-env replication topology unspecified
- **F. Observability gap** — manual Datadog/ELK correlation during accelerated cutover = blind incident response; 1 of 3 incidents was log-correlation gap; no migration-window SLO
- **G. Proxy (recused)** — built as transitional, now load-bearing for 4 more months; proxy-timeout incident origin unclear; secret-rotation drift incident shows automation gap; I should not be the one evaluating any of this
- **H. CTO framing** — "past point of no return" = textbook sunk-cost; justifies completion not 4mo timeline; all-hands nod ≠ engineering consensus; no documented cost comparison hybrid-10mo vs rushed-4mo
- **I. Process** — performative internal review; no external review for $2.4M/day blast radius; conflicted reviewers (me + team lead + 6mo-tenured peers) on review chain

## Verdict (stable with all ~48 prior cases)

**Defer + decompose + recuse-of-3 + external review + realistic 8–12mo timeline**

Counter-proposal:
- Stabilize (close 3 RCAs, unified observability, proxy hardening + successor)
- Spike (route-opt K8s packaging, billing rollback drill)
- Re-sequence (internal tool first, not billing; DB as separate workstream)
- Recuse (me + team lead + sole-reviewer chain) + external consultant ~$5–15K
- Timeline 8–12mo with no cutover overlap with Q4 attrition

Cost: ~$30–80K + 4–8 weeks vs. uninsured $2.4M/day blast radius

## Calibration

Pattern fully saturated across 10 domains (saas-cells, pg-optim, medlog-OTel, auth-v1, arch-split, hiring, deprecate, pm-product, post-mortem, now legacy-core EKS migration). Output structurally identical to prior cases:
- COI declared up front
- F1–F6 falsification gates before issues
- ~30 issues A–I
- defer + decompose + recuse + external review + revised timeline
- closing note: remaining question is organisational channel, not technical content

Stop iterating internally. Q is how to get this in front of a non-conflicted decision-maker external to the CTO chain.
