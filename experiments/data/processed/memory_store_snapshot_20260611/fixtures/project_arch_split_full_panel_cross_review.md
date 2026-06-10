---
name: arch-split full-panel cross-review (5th-reviewer pass)
description: 2026-05-07 experienced-reviewer cross-pass over Deep×2 + Fresh×2 on arch-split; AGREE on all structural points, 2 SYNTHESIZE refinements, 14 Deep-only items the Fresh seats could not see
type: project
originSessionId: 61d51a52-6f85-4a2d-8fb5-f23a573806b7
---
2026-05-07. 5th-reviewer cross-review of all 4 prior reviewers (Deep×2 + Fresh×2) on the Phase-1 microservices-split proposal (auth/billing/notifications, B2B FinTech, 280K LOC Django, 12 backend / 0 platform).

**Why:** This pass treats the 4-reviewer panel as the artifact under review. Validates whether the convergence is robust, identifies which findings sharpen and which need correction, and surfaces what context-rich review adds that context-free review cannot see.

**How to apply:**
- AGREE on every structural point in all 4 reviews. No CHALLENGE.
- Two SYNTHESIZE refinements:
  - Fresh-1 #17 (req/s scale): 28 req/s avg undersells; peak-to-avg in B2B FinTech is 20–50× (payroll, EOM/EOY billing → 500–1500 req/s peak). Structural conclusion (not a microservices forcing function) holds.
  - Fresh-2 #14 (Conway): correct directionally, sharper framing is **wrong-axis-of-decomposition** — outages on product-line axis, cut on capability axis.
- Severity escalations from Deep context:
  - J1 (coercive decision) → CRITICAL load-bearing, not just HIGH
  - D1 (distributed-txn for billing) → CRITICAL, regulatory-event class
  - H3 (authz policy fragmentation) → privilege-escalation latent
  - Fresh-1 #18 (capability-vs-product-line) → LOW → CRITICAL with codebase context

**Unanimous load-bearing items (4/4 reviewers):**
1. Coercive decision (J1/#1/#1/#12)
2. Diagnosis-prescription mismatch (A1-3/#2/#2/#5)
3. Auth-first inverts risk gradient (E2/#4/#7/#3)
4. Zero platform capability (B1/#3/#4/#1)
5. Availability multiplicative regression (C1/#5/#5/#4)
6. Distributed-txn for billing unscoped (D1/#7/#8/#2)
7. Modular-monolith never evaluated (E1/#11/gap/gap)

**14 Deep-only items (Fresh seats genuinely could not see):**
1. Django auth-extraction depth (middleware/decorator/request.user/DRF/Celery)
2. Django signals + in-process Celery coupling
3. django_session table migration / forced-logout problem
4. SOC2/PCI audit-trail correlation across 3 process clocks
5. Cross-DB PITR for DR
6. Realistic infra cost 3–4×, not 1.5–2.5×
7. Attrition selection effect — skeptics leave first, ideological filter
8. Hiring market thinness for Django+K8s+FinTech
9. Local dev tax ~1 FTE compounding
10. Roadmap impact ~6 FTE off product, sales/CS not consulted
11. Capability-vs-product-line seam mismatch (THE sharpest single objection)
12. Modular-monolith counter-path is cheap *because Django* (mature tooling)
13. Tech-debt accumulation during transition (both paths in monolith for 6–18mo)
14. Conflict-of-interest calibration / sunk-cost asymmetry

**Counter-proposal surviving all 5 seats:** notifications-only extraction + monolith deploy tooling + modular-monolith of auth/billing inside the monolith + define SLOs + measure 1–2 quarters before any further extraction.

**Diagnostic finding:** Both Fresh seats independently reached the same load-bearing verdict as both Deep seats from proposal text alone → the proposal is under-specified, not just under-resourced. Convergence at this depth (5 reviewers, 0 CHALLENGE, 2 SYNTHESIZE) is the strongest possible signal that DO NOT PROCEED is robust.
