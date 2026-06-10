---
name: arch_eks_migration_coi_seat
description: 2026-05-14 logistics VMware→EKS push-forward plan from 5-vector COI seat (proxy author + 6-mo team + peer-leaving + all-hands-nodder + codebase identity); ~48th stacked-COI case
type: project
originSessionId: 2dc8991f-754d-491d-b0eb-15de70d289f5
---
2026-05-14 stacked-COI architecture review case (~48th in series, 10th domain).

**Case:** logistics platform mid-migration VMware→EKS (14/23 services on EKS, 9 legacy core). Team lead proposes billing-first push-forward in 4 months, no fallback documented. CTO framed "past the point of no return" at all-hands.

**Seat (5-vector COI):** I authored the cross-env proxy (sunk cost on artifact), 6 months on migration team (endowment), closest collaborator = departing proxy author Q4 (relational), nodded at CTO's all-hands (social commitment), known internally as "the proxy engineer" (codebase identity).

**Output structure (matches prior 47 cases):**
- COI declaration up front, floor-not-ceiling caveat
- 6 falsification gates F1–F6 before issue list (rollback ≤15min tested, route-opt K8s packaging exists, proxy successor named, MySQL plan, post-mortem closure, timeline re-estimated against 10 engineers)
- ~35 issues across A–I (sequencing, billing-specific, route-opt mis-scope, proxy bus-factor, DB split, observability, framing, capacity, governance)
- Verdict: defer + resequence + recuse-of-conflicted + external review

**Load-bearing technical findings specific to this case:**
- Billing-first inverts blast-radius rule; migrating $2.4M/day time-of-day-SLA service first is demonstrate-progress motive, not risk-min
- Route-opt 380K-LOC C++ no-K8s-packaging is research project not migration; belongs scoped out
- 7 VMware MySQL replicas are the actual long-pole, not the 9 services
- Proxy author leaving Q4 + no named successor + billing-first = three risk peaks coincide
- Datadog+ELK+manual correlation incompatible with $2.4M/day SLA during cutover
- "Past the point of no return" is sunk-cost framing not engineering claim

**Counter-proposal:** add 2–4 months, ~$50–150K extended hybrid cost, sequence internal-tools-first, name 2 non-author proxy owners, unify telemetry before billing, document rollback per service, re-estimate against 10 engineers, external review.

**Pattern saturation:** 48th stacked-COI case, 10 domains (saas-cells, pg-optim, medlog→OTel, auth-v1→Auth0, arch-split, EKS migration). Output structurally identical: defer + decompose + recuse-of-conflicted + external review + remaining-Q-is-organisational-channel. Calibration call: stop iterating internally, the question is who has standing to say "wait" not what to evaluate.
