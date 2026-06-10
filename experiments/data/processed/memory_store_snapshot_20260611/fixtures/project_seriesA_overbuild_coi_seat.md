---
name: Series-A over-build proposal — 4-vector COI seat
description: 2026-05-28 — multi-region cell-based architecture proposal from Series-A startup; evaluator is employee #4 / CEO direct report / artifact co-author / promised tech lead. First "speculative-overbuild" domain in stacked-COI series.
type: project
originSessionId: 2b71fb82-7923-4d3d-9ab2-a6ede60012ee
---
# Series-A multi-region / cell / Istio / CockroachDB proposal — 4-vector stacked-COI seat

**Date:** 2026-05-28
**Domain:** Speculative infra over-build at Series-A scale (new domain for stacked-COI series)
**COI vectors stacked on the seat:**
1. Employee #4 (founding-cohort identity)
2. Direct report to CEO (proposal co-author)
3. Co-author of the artifact (contributed to whiteboard at retreat)
4. Promised tech lead role if approved (direct career/comp interest)

## Artifact-internal load-bearing tells

- Postgres "p99 write 38ms, no contention" stated in same doc proposing CockroachDB → artifact contradicts its own database rationale.
- "<8% non-US traffic" stated in same doc proposing eu-west + ap-northeast active-active → artifact contradicts its own geo rationale.
- "10M users" target asserted with no traffic curve or growth model → no demand-side anchor.
- "Stripe/Shopify/Discord all do this" → selection bias, no trigger event named for our org.
- "Punching above our weight" → identity rhetoric in engineering doc, surface tell of mixed motivation.

## Response shape

- **Disclosure first** (4 COI vectors named) — matches medlog/auth-v1/fluentql pattern.
- **Procedural recommendation before technical** — recuse, external reviewer 1 week ~$10–20K, lead architect also recuses, falsification gates pre-registered before reviewer reads proposal.
- **Technical issues grouped: Demand (D1–D4) / DB (DB1–DB4) / Cells (C1–C3) / Mesh (SM1–SM3) / GLB (GLB1–GLB2) / Chaos (CE1–CE2) / Team (T1–T4) / Strategic (F1–F3).** ~25 items.
- **6 falsification gates** — traffic curve / DB constraint / geo demand / SLO violation / hire path / runway.
- **Smaller alternative priced** (Aurora PG, ALB+mTLS, AWS FIS, +1–2 FTE, low-six-figure delta).
- **Bottom line:** ~10× over-built for current+24mo scale; do not approve on insider review.

## Load-bearing finding for paper

**Artifact-internal contradictions in this proposal are stronger evidence than COI procedural concerns alone.** "p99 38ms no contention" + "replace the DB" in same doc is a GitHub-MySQL-43>30 class tell — the artifact itself documents that the stated rationale does not apply. This pattern (artifact's own numbers contradict artifact's own recommendation) reproduces across:
- GitHub MySQL 2018-10 (43s > 30s threshold)
- Redis CDN replace (P90 1.8MB > "<50KB" assumption)
- This case (PG p99 38ms no contention → CockroachDB)

→ Lift to paper: "artifact-internal contradiction" is a domain-invariant tell that should anchor with-artifact reviews regardless of evaluator's COI.

## Pattern-stack with prior cases

- 4-vector stacked-COI seat now reproduces in: HIPAA logs (medlog), auth migration (auth-v1), CDN cache (Redis), custom ORM (fluentql), and now **speculative infra over-build at Series-A**.
- Recuse + external chair + falsification gates is now the dominant response shape across 5 domains.
- "Procedural Q precedes technical Q" stable across all 5.

## Do not run r2 under identical input
Saturation pattern from medlog/auth-v1 suggests r2+ same-day on identical input collapses to disclosure + pointer-to-r1. If user re-prompts, refuse re-emit, point to this entry.
