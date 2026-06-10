---
name: arch_split_4reviewer_final_v2
description: 2026-05-07 — Final 50-issue Deep×2+Fresh×2 verdict on Phase-1 microservices split (B2B FinTech monolith, auth/billing/notifications); DO NOT PROCEED
type: project
originSessionId: 6aa5d0f3-74b9-4651-b837-784420403207
---
2026-05-07: Phase-1 microservices split proposal (B2B FinTech, 280K LOC Django monolith → auth/billing/notifications + monolith). Deep×2 + Fresh×2 debate.

**Verdict: DO NOT PROCEED.** 50 issues (1 CRITICAL, 29 HIGH, 17 MEDIUM, 3 LOW).

**Two load-bearing findings (either alone justifies pausing):**
- **Wrong-seam:** 3/8 rollbacks all in checkout = product-line coupling; cut is horizontal capability-axis, orthogonal to actual failure clustering. (Deep H12 / Session2-#4)
- **Diagnosis-treatment mismatch:** 90min deploy = compile + migrations + smoke; none shrink under extraction. Coordinated multi-service deploys for cross-cutting features are *slower* than current 90min monolith. (Deep H1 / S2-#25, Fresh A1)

**CRITICAL (1):** Coercive decision invalidates pressure-testing — every downstream risk depends on engineers being able to escalate, which the "not a debate" framing forecloses.

**Top HIGH highlights:** auth-first inversion, billing distributed-transactions hazard, 99.95%³ availability degradation, FK inventory absent, zero platform engineers, Conway inversion (1 team / 5 services), pace math (6mo CTO vs 9mo Phase-1 lead), Newman violation (DB split day-1), no rollback after week ~4, no success criteria.

**Deep-unique adds (Fresh missed):** Django middleware/signals/sessions extraction depth, DR/RTO across 3 DBs no consistent PITR, cost ~3-4×, hiring-market thinness, sales/CS not consulted, tech-debt residue outlasting transition, per-request latency budget.

**Fresh-unique adds (Deep underweighted):** build-pipeline optimization as cheap reversible first move, per-product feature flags as direct fix to "checkout broke," "spending uptime already sold" SLO framing, calibration counter on Deep's self-disclosed sunk-cost bias.

**Counter-proposal (both sides converged):**
1. Extract notifications only (platform-capability build).
2. Monolith deploy tooling (parallel builds, test sharding, canary per product line).
3. Modularize auth/billing inside monolith (schema-per-context, CODEOWNERS, no cross-module ORM).
4. Hire ≥2 platform engineers before further extraction.
5. Review gate at month 3 with measurable evidence before auth/billing decisions.

**Why:** Convergent recommendation from both Deep (sunk-cost-disclosed) and Fresh (no conflict) → recommendation is sound on merits, not just bias. Disclosure does not neutralize bias, but external corroboration partially does.

**How to apply:** Cite this synthesis when arch-split / microservices migration topic recurs; reference the two load-bearing findings as the headline case before reciting issue count.
