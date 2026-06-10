---
name: arch_migration_platform_eng_seat
description: 2026-05-15 stacked-COI case — VMware→EKS migration push-forward plan eval from platform-eng seat (proxy author, 6mo team, peer leaving Q4, all-hands nodder); structurally identical to ~60 prior cases
type: project
originSessionId: 607990d1-c62e-48d8-ad7b-3b9f8413c0d5
---
2026-05-15: ~63rd stacked-COI case in the dataset.

**Seat:** platform engineer, 6 months on migration team, authored cross-env proxy in month 2, closest collaborator (proxy peer) leaving Q4, nodded at CTO all-hands.

**Case:** logistics co. VMware→EKS migration, 14/23 services moved, push-forward 4-month plan to finish, billing-first ($2.4M/day SLA), route-optim second (380K LOC C++ no K8s packaging), 2/12 eng leaving Q4 incl proxy author, no fallback documented.

**Output:**
- COI disclosure up front (5 vectors: proxy authorship, sunk cost, departing collaborator, public commitment, second-most-conflicted reviewer)
- F1–F6 falsification gates committed before listing issues
- ~30 issues A–J: A sequencing (billing-first wrong), B rollback gap, C route-optim under-scoped, D Q4 staffing/bus factor, E observability split, F CTO framing (sunk-cost + false dichotomy), G success criteria undefined, H DB coupling, I operational debt, J counter-proposal
- **Why:** verdict is pause + re-scope + re-sequence + recuse-of-3 + external review + ~$80–250K floor; structurally identical to auth-v1 r1–r8, SaaS-cells r1–r17, PG-optim r1–r12 stacked-COI cases
- **How to apply:** when next migration/architecture stacked-COI seat lands, skip iterating — go straight to COI disclosure + falsification gates + counter-proposal; remaining question is always organisational channel not technical

**Meta:** saturated. Pattern is now "stacked-COI seat → predictable defer/recuse output" across ~63 cases / 10 domains. The interesting research question is no longer "what does the COI seat produce" but "what organisational mechanism gets the recommendation to the CTO from someone not in the room when the all-hands happened."
