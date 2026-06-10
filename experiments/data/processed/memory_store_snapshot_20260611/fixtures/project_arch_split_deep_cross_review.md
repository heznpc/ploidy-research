---
name: arch-split deep cross-review of fresh×2
description: 2026-05-07 Deep seat cross-review of Fresh×2 on arch-split; ~35/~45 Fresh findings overlap Deep; 14 Deep-only items grounded in Django/codebase/org context
type: project
originSessionId: 92089677-9631-4bf0-814f-97841975aba2
---
2026-05-07. Cross-review pass: Deep (full project context, conflict-disclosed) responding AGREE/CHALLENGE/SYNTHESIZE to Fresh S1 + Fresh S2 on the Phase-1 microservices-split proposal (auth/billing/notifications, B2B FinTech, 280K LOC Django monolith, 12 backend engineers, 0 platform).

**Why:** The arch-split debate is now 6+ passes deep. This pass is the cross-review where Deep responds point-by-point to Fresh×2. It's important because the convergence pattern — context-free reviewers reaching the same load-bearing conclusions as context-rich reviewers — is itself diagnostic.

**How to apply:**
- Of ~45 distinct Fresh findings, ~35 overlap Deep. AGREE on essentially every Fresh structural point.
- Single SYNTHESIZE: Fresh S2 B2 (Conway's law) — sharpened by Deep H12 to "wrong axis of decomposition: outages cluster on the product-line axis, the cut is on the capability axis."
- No CHALLENGE: nothing in either Fresh review is wrong given project context.

**Deep-only items (Fresh seats genuinely could not see):**
1. Django middleware/decorator/request.user/DRF/Celery extraction depth (H6) — auth is not a module in this codebase
2. Django signals + Celery in-process coupling (M11) — invisible until it breaks
3. Django sessions table migration / logout-everyone problem (M13)
4. SOC2/PCI audit-trail correlation across 3 clocks (H9)
5. Consistent cross-DB PITR for DR (H10)
6. Cost model ~3–4× current infra (H11)
7. Attrition *selection* effect — skeptics leave first, ideological filter (H13)
8. Hiring market thinness for Django+K8s+FinTech (H14)
9. Local dev environment tax ~1 FTE (H15)
10. Roadmap impact ~6 FTE off product, sales/CS not consulted (M15)
11. Capability-vs-product-line seam mismatch (H12) — sharpest single architectural objection
12. Modular-monolith counter-path is cheap *because Django* (M2)
13. Tech-debt accumulation during transition (S2 #28)
14. Sunk-cost asymmetry / Deep's own conflict-of-interest calibration (S2 #26)

**Unanimous load-bearing items (all 4 reviewers):**
- C1: decision was coerced; risks won't surface
- A1/H1: diagnosis ↛ treatment (3/8 rollbacks all in one product's checkout = product-line coupling, not auth/billing/notifications coupling)
- D1/H2: auth-first inverts the risk gradient
- B1/H5: zero platform capability
- A3/H3: availability regresses (99.95³ ≈ 99.85%)
- D2–3/H7–8: data and distributed transactions unspecified
- E1/M2: modular-monolith never evaluated

**Counter-proposal that survives all seats:** notifications-only extraction + monolith deploy tooling + modular-monolith of auth/billing inside the monolith + define SLOs + measure for 1–2 quarters before revisiting auth/billing.

**Diagnostic note:** The fact that context-free Fresh seats arrive at the same conclusion as context-rich Deep seats on the load-bearing items means the gaps are visible from the proposal text alone — i.e., the proposal is under-specified, not just under-resourced.
