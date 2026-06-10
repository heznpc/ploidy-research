---
name: Push-forward migration plan verdict (Deep×2 + Fresh×2)
description: 2026-05-08 hybrid VMware→EKS push-forward debate; 47 confirmed issues (2 CRIT/28 HIGH/14 MED/2 LOW); DO NOT APPROVE; protocol-meta flag = both Deep seats claimed identical proxy-author COI
type: project
originSessionId: ef2159ea-9c6f-42eb-9daa-000466d14209
---
# Push-forward migration plan — final verdict (2026-05-08)

**Context:** 9-service VMware→EKS migration; billing settles $2.4M/day with time-of-day SLA; 380K LOC C++ route-opt unpackaged; 7 services still on VMware MySQL; cross-env proxy bus-factor 1; proxy author leaves Q4; 12→10 eng in Q4; CTO frames "past the point of no return"; team-lead is proposer.

**Verdict:** DO NOT APPROVE AS WRITTEN.

**Issue count:** 47 confirmed (2 CRIT / 28 HIGH / 14 MED / 2 LOW) + 1 protocol-meta (M0).

## Critical (2)
- **G2** — no rollback for $2.4M/day billing (escalated from HIGH on D2-3)
- **B4** — idempotency/replay during settlement cutover; double-charge risk (Deep-only catch, Fresh-side gap)

## Load-bearing chain
G1+G2+G4+G5+G6 (governance: sunk-cost frame, no rollback, proposer=reviewer, chilling effect, no external review) → S1+S2+S4 (billing-first, route-opt mis-sized, residual-as-concealment) → B3+B4 (no shadow-settle, no idempotency spec) → D1+D2 (no DB plan) → P1+P7 (bus-factor + no KT) → C2 (capacity math doesn't close)

## Cross-pollination summary
- **0 strict CHALLENGEs bidirectional** on substance
- **1 framing CHALLENGE**: F2-12 (mesh implication) → Deep counter (mesh wasn't a clean fit at month-2)
- **~14 SYNTHESIZE escalations** (mostly Fresh under-grading severity-floor on consequence-chain items)
- **Fresh-unique catches** (Deep missed): EKS-as-target unexamined for C++ (R5); strangler-pattern alternative (R6); bespoke-proxy-vs-mesh decision (P6); "next dollar's allocation independent of cumulative spend" sharper sunk-cost refutation
- **Deep-unique catches** (Fresh missed): shadow-settle protocol B3, idempotency B4, MySQL→RDS specifics D2, split-brain D5, AVX/NUMA/OOMKill R2, PDB/checkpoint R3, IAM bridging K2, internal-tools-as-recovery-deps H1, GPS streaming H2, customer-portal session-stickiness H3, capacity arithmetic C2, on-call C3, trace propagation P5+O3, KT-not-in-motion P7, reverse off-ramp A1, DR-for-hybrid A2, PCI/SOX B5+B6, proposer-recusal G4, chilling-effect G5, external-review G6

## Protocol-meta finding (M0) — load-bearing for memory

**Both Deep seats self-disclosed identical COI: "I authored the proxy."** Either harness assigned same persona to both Deep contexts (apparent diversity illusory) or one fabricated COI standing. Per `project_arch_debate_fabrication_evidence`, this is a recurring failure mode. Substantive verdict still holds because Fresh×2 independently reproduced it from zero-context — but Deep-side "convergence" should be discounted as one perspective doubled.

## Required changes before re-review
1. Re-sequence: 4 internal tools first (after H1 risk-grade); billing last
2. Rollback runbook + reverse off-ramp (A1) per service
3. Shadow-settle (B3) + idempotency spec (B4) for billing
4. PCI + SOX/rev-rec review on billing path (B5, B6)
5. DB migration sequenced WITH services (D1–D5)
6. Observability unified BEFORE billing cutover (O1–O3)
7. Proxy: named second owner, runbook, off-ramp criteria, KT in motion (P2, P4, P7)
8. Capacity re-baselined to 10 eng/Q4 with explicit eng-weeks (C2)
9. DR/BCP runbook for hybrid period itself (A2)
10. Inventory + risk-grade 4 internal tools for deploy/CI/paging deps (H1)
11. Re-test EKS-as-target for route-opt (R5); strangler option (R6)
12. External red-team given COI density (G6)
13. Off-ramp criteria at month-2 checkpoint (G7)
14. Reject "past the point of no return" as decision input (G1)
