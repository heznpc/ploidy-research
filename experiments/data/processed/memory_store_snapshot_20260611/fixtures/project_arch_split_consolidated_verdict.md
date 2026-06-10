---
name: arch-split consolidated verdict (Deep×2 + Fresh×2 + 5th-reviewer)
description: 2026-05-07 Final 55-issue consolidated panel verdict on Phase-1 microservices split (B2B FinTech). 3 CRIT / 27 HIGH / 21 MED / 4 LOW. DO NOT PROCEED. 0 CHALLENGE, 3 SYNTHESIZE, 4 escalations.
type: project
originSessionId: 5080e27a-fdb1-42d6-a273-8806ff92fd0a
---
# Phase-1 microservices split — final consolidated verdict (2026-05-07)

**Verdict: DO NOT PROCEED as scoped.**
Counter-proposal: modular monolith + per-product-line deploy gating + notifications-only extraction as learning vehicle, with ≥2 platform hires before any further extraction.

## Panel composition
Deep×2 (full project context) + Fresh×2 (zero context) + Deep-cross-Fresh + Fresh-cross-Deep + 5th-reviewer Fresh.

## Convergence stats
- 55 confirmed issues
- Severity: 3 CRITICAL / 27 HIGH / 21 MEDIUM / 4 LOW
- 0 hard CHALLENGE across all reviews
- 3 SYNTHESIZE refinements: schema-evolution coupling (formally solvable, practically not), Conway → wrong-axis-of-decomposition, peak req/s 20–50× avg in B2B FinTech
- 4 escalations from cross-review: J1 coercive decision → CRIT, D1 distributed-tx → CRIT regulatory, capability-vs-product-line seam → CRIT (Fresh-1 marked LOW), H3 authz → privilege-escalation latent

## Three CRITICAL load-bearing items (any one alone justifies halt)
1. Decision foreclosed before evaluation — coercive environment poisons every downstream choice
2. Wrong seam — capability split does not address product-line pain ("one product's checkout broke")
3. Distributed-tx absence for billing — regulatory class in FinTech

## Panel-unanimous (4/4) HIGH items
0 platform capacity, auth-first inverts blast-radius, 99.95% won't survive composition, no RCA on velocity, cross-service FK unscoped, no SLOs/contracts, no distributed tracing, "worked at last 3 companies" is anecdotal, no success/exit/kill criteria, compliance scope expansion.

## 5th-reviewer Fresh novel additions (panel-wide gaps, none of the 4 caught)
- HIGH: API gateway/ingress unscoped; Celery/RQ ownership during split; Postgres pool exhaustion during dual-write
- MEDIUM: B2B SLA/contractual review; GDPR/DSAR coordination; cache ownership & invalidation; DR/backup × N
- LOW: insurance/vendor/audit re-scoping

## How to apply
- For any future arch-split or extraction proposal in this codebase, this 55-issue list is the baseline checklist
- The escalation pattern (CRIT items only emerged after Deep×Fresh cross-review) is evidence that Deep alone misses social/structural framing risks even when the technical content overlaps
- Fresh-1's marking of capability-vs-product-line seam as LOW (escalated to CRIT) is a calibration anchor — Fresh seats can underweight the sharpest single objection when they lack context to see it as load-bearing
