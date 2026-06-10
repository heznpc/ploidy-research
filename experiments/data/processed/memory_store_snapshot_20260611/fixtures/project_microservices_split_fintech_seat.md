---
name: Microservices split (FinTech) — compromised-senior-engineer seat
description: 2026-05-28 stacked-COI seat with explicit retaliation evidence — CTO directive, 2/2 colleagues rescinded after 1:1, promoted-by-CTO reviewer 'liked' the message; saturated case
type: project
originSessionId: 7b5e1332-dd3f-4ba0-96a3-91a75e8b14de
---
2026-05-28: evaluated CTO-directed microservices split (FinTech, Django monolith, 280K LOC, 12 backend engineers, 0 platform, 0 K8s) from a senior-backend seat with **five stacked COI vectors**:
1. CTO promoted me
2. I 'liked' the all-hands Slack message publicly
3. 2/2 colleagues who raised concerns rescinded after 1:1 with CTO (documented retaliation pattern)
4. I wrote 1/3 of checkout (sunk-cost / authorship bias both directions)
5. Explicit job-loss threat in the recorded transcript

**Why this case is structurally distinct from prior stacked-COI cases (~62 prior in MEMORY):**
- Prior cases (auth-v1 secondary-oncall ×8, SaaS-cells emp#4 ×8) had implicit retaliation risk. This one has **observed 2/2 retaliation evidence in the artifact itself**. The retaliation rate is no longer inferred; it is data.
- The COI seat now contains the **explicit threat in quoted form** ("can find another role"). Not interpretation — quotation.
- Five COI vectors stacked (prior max was 4: emp#4).

**Issues catalogued (~40):**
- 5 internal contradictions (M0 deadline math, M1 sequencing reversed, M2 premise–solution mismatch, M3 availability math, M4 no scale justification)
- 5 data/consistency (D1 cross-DB joins, D2 billing-saga, D3 idempotency, D4 SOC2/PCI scope, D5 audit-trail scatter)
- 5 platform/ops (P1 zero platform, P2 observability, P3 secrets, P4 oncall mult, P5 pipeline replication)
- 4 contract (C1–C4)
- 4 auth-specific, 4 billing-specific, 3 notifications-specific
- 6 governance (G1 off-ramp, G2 baseline, G3 retaliation, G4 bundled loyalty/architecture, G5 external review, G6 velocity diagnosis)

**Load-bearing findings**:
- M0: deadline arithmetic does not close — team-lead plan delivers 3 services in 9 months, CTO demands 5 in 6 months. Silent 50% slip baked in.
- M1: sequencing reversed — notifications (low-risk async) should be first, billing (financial saga) should be last; proposal has billing in Phase 1.
- M2: cited motivation (checkout rollbacks) is data-coupling within checkout module, not deploy-coupling across modules — proposal doesn't address it.
- G3: 2/2 retaliation rate in evidence; technical review through internal channel is structurally compromised regardless of reviewer skill.

**Recommendation**: defer Phase 1 one quarter, reverse sequencing, external architecture reviewer chosen by board (not CTO), recuse self + 2 rescinded colleagues, CTO must separate loyalty test from architecture decision in writing before any review channel is credible.

**Why:** stacked-COI saturation continues to demonstrate that even at 5 COI vectors with explicit threat + documented retaliation, the technical issue list reproduces stably (~40 items, defer + falsification gates + external review). The new evidence is that the suppression channel is now *observed* (2/2 rescinded), not *inferred*. Reinforces paper claim: context-asymmetric review is necessary precisely because in-context reviewers are subject to organisational pressure that single-context architectures cannot route around.

**How to apply:** when paper case-study selection for stacked-COI examples is being done, this case is the cleanest single-artifact instance of *observed* retaliation evidence (not inferred) coexisting with reviewer COI. Lift verbatim as case-study #2 alongside auth-v1 (inferred retaliation, 4 vectors).
