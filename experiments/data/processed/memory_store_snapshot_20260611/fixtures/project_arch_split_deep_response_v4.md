---
name: arch-split Deep×2 → Fresh×2 cross-review (v4)
description: 2026-05-07 second Deep×2 per-point response to a different Fresh×2 set (40 points) on Phase-1 microservices split; ~38/40 AGREE, 0 CHALLENGE, 7 SYNTHESIZE escalations, 18 Deep-only items
type: project
originSessionId: f03ca8b9-71ae-43e5-a6d3-b0008831c40a
---
# arch-split Deep×2 → Fresh×2 response (v4, 2026-05-07)

## Context
Distinct Fresh×2 + Deep×2 pass on the same Phase-1 split proposal (auth/billing/notifications) at B2B FinTech, 280K LOC Django monolith, 12 backend / 0 platform engineers, 4 product lines, 99.95%/18mo uptime, CTO directive ("not a debate"), 2 dissenters rescinded.

This is the second cross-review session (cf. v3 which was a 30-point pass with different Fresh content).

## Headline
- 40 Fresh×2 points, **0 CHALLENGE**, 7 SYNTHESIZE (severity escalations), ~33/40 AGREE.
- ~30/40 overlap with Deep×2 (strong reproducibility without project context).
- 18 Deep-only items, almost all Django-specific structural coupling or governance/finance.

## Fresh-unique catches Deep should adopt
1. Availability math: 99.95³ ≈ 99.85% optimistic; realistic year-1 product ≈ 99.5%. Quantifies B2B SLA breach.
2. 2.4M req/day anchor for billing dual-write + backfill window.
3. "Output target, not outcome" framing for "5 services in 6 months."
4. "9 likes are not endorsement evidence under these conditions."
5. MTTR regression as observability concern.
6. "Independent deploy is theoretical without contract tests" — without consumer-driven contracts, services deploy in lockstep and the entire premise evaporates.
7. Selection bias in CTO claim ("CTO got hired again, so prior outcomes were tolerable to him").
8. "In fintech, checkout latency moves conversion" — revenue framing.

## Severity escalations (MEDIUM → HIGH)
- One-quarter timeline given 0 platform precedent
- PCI scope expansion (B2B FinTech)
- Conway's Law mismatch (load-bearing diagnostic error)
- Availability math (B2B SLA breach)
- Compliance/audit boundary changes
- Feature flags / canary missing (the cheap fix that wasn't tried)
- On-call staffing for 5 service rotations with 12 engineers

## Deep-only items Fresh×2 missed
1. Django signals (`post_save`/`pre_save`) cross app boundaries → need bus + outbox
2. Cross-app ORM queries (`User.objects.filter(billing_account__plan='enterprise')`) → silent break or N+1 over HTTP
3. Django admin used by Ops/CS for support — 3 sites or unified portal, neither scoped
4. Custom managers/querysets spanning apps — won't survive split
5. GDPR / DSAR "delete user X" as orchestrated multi-service deletion
6. `auth.Permission` → `ContentType` FK to every model — extracting auth requires permission-system redesign
7. Django sessions (`django_session` table) live in monolith DB — Redis SPOF / JWT migration / cookie-domain SSO required
8. Login + audit + welcome-email + billing record = one transaction today
9. Refund + audit + notification = one transaction today
10. Reconciliation jobs DB-transaction atomic (Celery + Postgres guarantees)
11. Attrition selection bias — "find another role" pushes out monolith experts
12. Decision recusal — team lead reports to CTO; need external architectural review
13. Conflict-of-interest disclosure within the review itself (1/3 of checkout authored, rescinders adjacent)
14. Opportunity cost in dollars (~$1.2–2M loaded for 12 eng × 6 mo)
15. No off-ramp / abort criteria
16. Hiring pipeline + ramp = 6+ months — won't fit inside the 6-month window
17. PG connection pool blow-out across services without pgBouncer
18. No Phase-2 architecture / end-state diagram → Phase 1 may be sunk cost

## Why this matters for the ploidy paper
- Fresh×2 with **no project context** independently reproduce ~75% of Deep findings — strong evidence Deep's findings are not project-context-bias artefacts.
- Fresh-unique catches are quantification + meta-framing (clean external math, no anchoring on internal facts).
- Deep-unique catches are Django-specific structural coupling, governance, finance.
- Sides are **complementary, not redundant**: Deep without Fresh misses availability math and contract-test premise; Fresh without Deep misses Django signals/permissions/admin coupling.

## Convergent verdict
DO NOT PROCEED with Phase-1 as proposed. Counter-proposal: modular monolith + online schema change + notifications-only extraction + ≥2 platform engineers + external architectural review.
