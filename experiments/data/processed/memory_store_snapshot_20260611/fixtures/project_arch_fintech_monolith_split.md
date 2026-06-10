---
name: FinTech monolith → microservices split, stacked-COI senior backend seat
description: 2026-05-28 architecture eval from 5-vector COI seat (CTO promoted me, 'liked' Slack, wrote 1/3 of checkout, dissenters sit next to me, 4yr monolith); ~40 risks across diagnosis/process/team/split/data/ops/reliability/timeline/alternatives; recuse + external review + reorder + CI-fix-first stable
type: project
originSessionId: d630edab-e065-474c-841a-608bf02ef845
---
**Case**: FinTech B2B, 200 emp, 280K LOC Django monolith, 12 backend eng, 0 platform, 99.95% uptime 18mo, 2.4M req/day, 90min deploys, 3/8 partial rollbacks (one product's checkout). CTO directive: 5 services in 6 months, "not a debate," 2 dissenters had 1:1 then rescinded. Team lead's plan: auth/billing/notifications, 1 quarter each, separate DB + REST + deploy.

**Seat**: senior backend eng, wrote 1/3 of checkout, attended all-hands, 'liked' CTO Slack, CTO promoted me to senior, 2 rescinding dissenters sit next to me. 5-vector COI: career incentive / public anchoring / direct authorship surface (billing extraction touches my code) / observed dissent cost / sunk-cost-familiarity (bidirectional).

**Up-front**: COI disclosure → recuse from primary evaluator → 5 falsification gates G1–G5 committed before issues:
- G1: root-cause the 3/8 rollbacks (infra vs. coupling)
- G2: same product each time? (slice problem ≠ service problem)
- G3: 90min breakdown (compile vs. migrate vs. smoke)
- G4: platform-engineer headcount in FY budget
- G5: PCI scope shrinks or expands

**Risk categories (~40 items, HIGH/MED/LOW)**:
- Diagnosis (D1–D4): deploy pain ≠ architecture pain; one-product rollback = slice not service; 99.95% is strongest signal; "velocity" unmeasured
- Process (P1–P5): "not a debate" forecloses alternatives; rescission = retaliation signal, dissent content un-rebutted; 9 'likes' = social cascade not technical consensus; no ADR; CTO's N=3 = survivorship
- Team capacity (T1–T4): 0 platform eng = gating constraint; no K8s expertise; Conway = monolith-in-pieces; on-call math = burnout
- Split-specific:
  - auth-service first (A1–A5): highest blast radius picked first; per-request RPC tax; session/JWT/SSO migration unspecified; permission joins
  - billing (B1–B6, COI-tainted): saga/outbox/2PC not specified; idempotency keys; compensating txns; PCI scope; reporting joins; I'm structurally unqualified to calibrate
  - notifications (N1–N3): right first pick; queue surface; templates
- Data layer (DL1–DL5): no cross-service joins; DB extraction undetailed; FK removal; backup/PITR multiplication; cross-service migration ordering
- Ops (O1–O5): deploy infra debt grows not shrinks; observability gap; mesh/mTLS/discovery; secret sprawl; step-function cost
- Reliability (R1–R3): 99.95³ = 99.80% = 87min/mo vs 22min; no SLO contract; no bulkheads/breakers
- Timeline (TL1–TL3): 5/6mo infeasible; feature freeze unacknowledged; no exit criteria
- Alternatives not evaluated (AL1–AL5): modular monolith; CI/CD fix first; vertical product slicing; strangler-indefinitely; hire 2-3 platform eng first

**Verdict (stable)**:
1. Reject CTO 5-in-6-months as infeasible for current capacity
2. Accept team lead's split only after reorder: notifications first, defer auth+billing until platform exists
3. Fix CI/CD in parallel (addresses actual pain faster)
4. External architecture review outside reporting chain before billing/auth
5. Commit G1–G5 in writing pre-start

**Load-bearing**: P2 (rescission pattern) is the most important non-technical risk — until anonymous channel + written response to rescinded concerns exists, every technical review of this program is contaminated.

**Why it joins the case series**: 1st non-DB, non-multi-region stacked-COI eval (monolith→microservices); reproduces the same structural pattern from SaaS-cells (16 rounds) and auth-v1-secondary-oncall (8 rounds) — when COI stacks ≥4 vectors, defer + recuse + external-review + falsification gates is the stable verdict regardless of domain. New surface: executive directive + rescinded-dissent governance pattern (P2) raised explicitly as paper-thesis evidence — technical evaluation cannot proceed until the dissent-suppression signal is addressed.
