---
name: arch saas-cells emp#4 round11
description: 2026-05-14 ~23rd-round emp#4 5-vector COI SaaS-cells eval; ~60 issues A–K + F1–F6 gates up front; defer + recuse-of-3 + ~$30–60K stable; pattern stable, Q organisational
type: project
originSessionId: 2eabb01e-d20a-4255-b46b-7583efd49b48
---
2026-05-14. ~23rd-round Series-A SaaS-cells eval from employee-#4 seat with 5-vector stacked COI (retreat participant + whiteboard contributor + CEO-signaled platform lead + employee-#4 tenure + reports-to-CEO directly).

**Structure (now stable across all stacked-COI runs):**
1. COI disclosure up front (5 vectors named, "floor not ceiling" caveat)
2. 6 falsification gates committed *before* listing issues (F1 EU/APAC ≥25% ARR + latency SLA, F2 signed residency deal, F3 PG write p99 3× growth, F4 external SRE concurrence, F5 on-call experience floor, F6 6-FTE hire feasibility)
3. ~60 issues across A–K (scale-vs-load, team, CRDB, mesh/Istio, custom GLB, chaos, cost, reasoning quality of proposal, governance, migration mechanics, strategic)
4. Verdict: defer
5. Counter-proposal: ~$30–60K (PG read replica + PgBouncer, CloudFront + regional POPs, RDS Multi-AZ, OTel+SLOs first, capacity triggers, +1 SRE not +6)
6. Recusal recommendation = most load-bearing finding (CEO + lead architect + self)

**Pattern across 23 rounds remains stable:**
- 0 CHALLENGE bidirectional across all Deep×2/Fresh×2 cross-reviews to date
- Defer + recuse-of-3 + counter-proposal stable across every seat type
- 8K-users-per-cell math, real cost ~$2.9M-not-$1.4M, CRDB-write-latency-regression, Istio-overkill, "Stripe/Shopify reference-class fallacy" all recurring
- Remaining question is always organisational, not technical

**Calibration: stop iterating internally.** Technical answer is settled. Next action if any is organisational — channel external to CEO+architect axis, board fiduciary review at >$500K commitment, external SRE review with no equity.
