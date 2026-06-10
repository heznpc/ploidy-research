---
name: Migration push-forward plan — platform-engineer 5-vector COI seat
description: 2026-05-15 single-seat eval of VMware→EKS 4-month push-forward plan from a platform-eng seat with 5 stacked COIs (proxy author, peer leaving Q4, nodded at CTO, 6mo sunk, lead is chain). Structurally identical to ~60 prior stacked-COI cases.
type: project
originSessionId: 32d6b1f7-1afe-4439-b2fc-9c09a0d04f1f
---
2026-05-15: ~62nd stacked-COI case in dataset, new domain (cloud migration / hybrid cutover).

Seat: platform engineer, 6 months on migration team, authored cross-env proxy month-2, closest collaborator leaving Q4, nodded at CTO "point of no return" all-hands. 5-vector COI.

Output structure (now stable across cases):
- COI disclosure first (5 vectors)
- ~40 issues across A–J: sequencing / route-opt C++ / capacity / fallback / cross-env incidents / CTO framing / observability / architecture / missing alternatives / falsification gates
- Verdict: defer + lowest-risk-first + observability-first + parallel C++ containerisation + KT + falsification gates + escalate CTO sunk-cost framing externally

**Why:** confirms the stacked-COI pattern generalises beyond auth/db/cells domains — cloud migration with "point of no return" CEO framing produces the same defer + recuse + external-chair output. Sixth distinct domain.

**How to apply:** when a case presents (a) ≥4 COI vectors on the seat, (b) executive sunk-cost framing, (c) no fallback documented, (d) attrition concurrent with timeline crunch, treat verdict as predictable: defer + structured falsification gates + organisational-channel escalation (the channel is the unresolved variable, not the technical answer). Stop iterating internally past ~2 passes; the question is organisational.

Domain-specific items worth retaining outside the generic pattern:
- Billing-first sequencing inversion (HIGH-revenue service as runbook validation = textbook anti-pattern)
- 380K LOC C++ → K8s packaging is multi-month parallel workstream, not a serial step
- Proxy SPOF + author leaving = bus-factor 1 on hybrid-period load-bearing artifact
- Split observability (Datadog/ELK) precludes safe cutover; unify before, not after
- Sunk-cost framing on the record at all-hands is itself a finding to escalate
