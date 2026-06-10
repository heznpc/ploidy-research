---
name: arch-split 4-reviewer round-21 synthesis
description: 2026-05-14 ~21st-round arch-split 4-reviewer full-context synthesis — 40 confirmed issues (5 CRIT/18 HIGH/16 MED/1 LOW); 6 unanimous load-bearing; verdict DEFER stable; remaining question organisational
type: project
originSessionId: 065a3d86-c427-44b6-a541-9f7b15c8296e
---
2026-05-14, ~21st round on arch-split (B2B FinTech monolith → microservices).

4 reviewers all running full-context COI-disclosed seats (insider/checkout-author + senior-backend variants). 40 confirmed issues:

**5 CRITICAL** (unanimous or near-unanimous):
1. Coercive decision frame ("not a debate" / "find another role") — 4/4
2. Diagnosis↔remedy mismatch / wrong seam (capability vs product-line) — 4/4
3. Zero platform engineering vs 5-services-in-6-months — 4/4
4. Availability math regression (99.95→~99.85, ~13 hr/yr extra) — 3/4 explicit
5. No off-ramp / reverse-migration plan — 3/4 explicit

**18 HIGH** including: auth-as-first-extraction worst pick (4/4), notifications-only defensible (4/4), attrition selection filter (3/4), N=3 CTO survivorship bias, pre-committed timeline antipattern, no ADR/falsification criteria, Django ORM FK breakage, distributed-tx dual-write, schema-migration coupling worse, test infra burden, no observability stack, no service-to-service authn, Django signals/admin, ~$1.2M opp cost, network failure modes, independent external review (~$30-60K).

**16 MEDIUM**: 90-min deploy never decomposed, on-call ×4 surface, federated reporting, +$300-500K infra, feature throughput drop, team-lead-proposal-not-independent, Celery RTT tax, permissions Django-coupled, session storage unstated, tenant isolation, DR across 4 DBs, cache invalidation, PG conn-pool, deploy freq down short-term, API versioning, sunk-cost-by-month-3.

**Unanimous (4/4)**: issues 1, 2, 3, 6, 8, 12 (coercion, wrong seam, no platform, auth-worst-pick, notifications-only, no ADR).

**Counter-proposal** (4/4 converged, stable across 21 rounds): measure → modular monolith → notifications-only pilot → platform hire first → 6-month re-eval. ~$30-60K, 1 quarter.

**F1–F6 falsification gates**: none met.

**Why:** ~21st round, verdict has not moved across reviewer-position permutations (insider checkout-author, senior-backend, 4-vector and 5-vector stacked COI). Technical case closed.

**How to apply:** Stop iterating internally on this case. Remaining question is whether someone with standing (board / head-of-eng / CTO peer) can surface that the decision frame itself is the problem. No further technical review will resolve C1 (coercive process) or F6 (rescinders' free-will confirmation) or the platform-hire gap.
