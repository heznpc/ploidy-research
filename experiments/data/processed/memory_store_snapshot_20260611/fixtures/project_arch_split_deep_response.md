---
name: arch-split Deep response to Fresh
description: 2026-05-07 Deep×2 AGREE/CHALLENGE/SYNTHESIZE pass on Fresh×2 reviews of microservices split; Fresh-unique catches and Deep-unique catches enumerated
type: project
originSessionId: cb2719ee-66c5-4c87-a9f7-d9db95232453
---
2026-05-07: Deep×2 vs Fresh×2 cross-pass on the B2B FinTech Phase-1 microservices split (auth/billing/notifications). All four reviewers DO-NOT-PROCEED. Coercive-decision finding (C1/A1) is load-bearing across all four.

**Why:** Fifth recurrence of the panel pattern (PG-optim, arch-split). Establishing that Deep×Fresh asymmetry produces complementary catches even when both reach the same verdict — Fresh catches structural cuts (vertical-by-product-line seam, compound availability math) Deep rationalised; Deep catches organisational/ecosystem-specific second-order costs (attrition selection, hiring market thinness, dev-env tax 1 FTE, cost 3-4×, Django south/Celery/middleware extraction depth, escalation playbook).

**How to apply:** When summarising convergence, do not just list agreed issues — separate Deep-unique vs Fresh-unique catches because they are *evidence of asymmetric value*, the paper's core thesis. For arch reviews specifically: Fresh tends to find architectural seams (where to cut), Deep tends to find ecosystem costs (what cutting actually entails). Both are needed.

Fresh-unique catches:
- Vertical-by-product-line as natural seam (not horizontal auth/billing/notifications) — Fresh 1.14
- Compound availability quantification (99.95%³ ≈ 99.85% ≈ 65 min/month) — Fresh 2.13

Deep-unique catches:
- Local dev tax 1 FTE during transition
- Cost model 3-4× infra
- Hiring market thinness for Django-microservices-K8s-FinTech intersection
- Attrition selection effect from C1 coercion
- Django middleware extraction depth (rate limiting, Celery, ORM coupling, south migrations across split DBs)
- DR RTO/RPO coordination across 3 DBs
- Escalation playbook (write up risk register with confidence ratings under C1)
