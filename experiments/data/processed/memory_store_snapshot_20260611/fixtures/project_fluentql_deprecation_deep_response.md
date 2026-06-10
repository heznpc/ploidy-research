---
name: fluentql deprecation — Deep×2 → Fresh×2 cross-review
description: 2026-05-07 cross-review of Fresh×2 on fluentql deprecation decision; 0 CHALLENGE, 2 SYNTHESIZE, 28/28 AGREE; Fresh-unique = blast-radius × 5 products, no rollback plan, "status quo isn't safe", "teach better has been the 6-year experiment", net-assessment framing; Deep-only = recusal-not-raised in minutes, code-review authority asymmetry, chilling effect, attrition-as-coercion, B1 social-graph cross-check
type: project
originSessionId: ccdfe9e0-fed4-4c72-a26a-99df16d96ff7
---
# fluentql Deprecation: Deep×2 → Fresh×2 Cross-Review

Date: 2026-05-07
Topic: 4-3 vote to delay deprecation of fluentql (47K-LOC in-house Python ORM, no async, custom migrations, 4 prod incidents/yr, 11/14 engineers cite onboarding pain). Author Ji-Hye cast swing vote.

## Verdict pattern
- 0 strict CHALLENGEs (Deep on Fresh, this round)
- 2 SYNTHESIZE (F1-3 promote 2× claim to HIGH; F1-9 promote migration-tooling MEDIUM→HIGH; F1-14 doc-as-alternative is real but understated cost)
- 28/28 (or thereabouts) AGREE on technical/governance core

## Fresh-unique catches Deep missed
1. F2-12: 5-product blast-radius multiplier on shared data layer (4 incidents × 5 products)
2. F2-14: No success criteria / rollback triggers in migration plan — gives a *legitimate* revision lever vs. delay
3. F1-14: Status quo is not the safe option — do-nothing baseline is a risk position
4. F2-5 sharpening: "Teach better" has been the 6-year experiment that produced 4 incidents/yr + 79% pain
5. F2 net-assessment: "Approve in principle, require hardened plan" — sharper than Deep's "deprecate with migration period"

## Deep-only items Fresh structurally couldn't see
1. Committee minutes don't show whether recusal was raised (procedural contamination, not just COI)
2. Asymmetric authority — Ji-Hye approves participants' code reviews → 3 dissenters structurally suppressed
3. B1 self-disclosure as cross-check methodology — reviewer onboarded by Ji-Hye, shipped 6 features, abstained; convergence against social interest is load-bearing
4. Chilling effect on future deprecation proposals (governance precedent)
5. Selection bias in "edge cases" — when 79% hit them, they're the surface
6. Phased plan already mitigates Ji-Hye's stated risk (her objection is to unphased rewrite that wasn't proposed)
7. Attrition-as-coercion — using "Ji-Hye may disengage" as delay justification is itself coercive

## Severity-floor pattern
Fresh-1 graded migration-tooling MEDIUM; Deep + Fresh-2 graded HIGH. Same severity-floor under-grading on consequence-chain items observed across Redis-as-CDN rounds.

## Deep / Fresh complementarity
- Fresh-unique = plan-side (rollback gates, blast-radius math, status-quo-isn't-free)
- Deep-unique = governance/social-graph (recusal-not-raised, code-review authority, chilling effect, attrition coercion)

## Consolidated recommendation
**Approve in principle, require hardened plan; do not delay.** Re-vote with Ji-Hye recused, benchmark against SQLA 2.0 + asyncpg on actual workload, present carrying-cost ledger (incidents × 5 products + onboarding + async ceiling + bus factor) on the do-nothing side.
