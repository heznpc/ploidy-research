---
name: fluentql Deep×2 → Fresh×2 cross-review v2
description: 2026-05-07 second Deep×2 cross-review of Fresh×2 on fluentql delay; 0 CHALLENGE bidirectional, 5 SYNTHESIZE severity escalations (Fresh severity-floor pattern); 2 Fresh-unique catches Deep missed (DSL security/SQL-injection surface F2-12, symmetric scrutiny on 2-quarter estimate F1-10, missing 11-engineer voice F1-15); 8 Deep-only items (recusal-not-raised in minutes, code-review authority asymmetry CRITICAL, attrition-as-coercion, chilling effect, phased plan already mitigates objection, edge-case selection bias, net-of-incident cost both-sided, builder COI cross-check methodology); verdict stable = approve in principle + hardened plan, do not delay
type: project
originSessionId: a21e7044-71b9-4380-85d6-65f61557e1b8
---
# fluentql delay decision — 2nd Deep×2 → Fresh×2 cross-review

Date: 2026-05-07

## Pattern (matches arch-split, Redis-as-CDN, pg-optim)
- 0 strict CHALLENGEs bidirectional
- 5 severity-floor SYNTHESIZE escalations on Fresh consequence-chain items
- ~80% overlap with prior Deep×2

## Severity escalations recommended
- F2-3 no counter-proposal: MEDIUM → HIGH
- F2-6 / F1-5 no async: MEDIUM → HIGH
- F2-10 phased plan under-specified: LOW → MEDIUM
- F1-13 strangler-fig alternative: LOW → MEDIUM (it's the POC counter-proposal)
- F1-14 open-ended delay = rejection: MEDIUM → HIGH

## Fresh-unique catches Deep missed
1. F2-12: DSL security / SQL-injection surface of custom 47K LOC parser — no CVE pipeline, no community fuzzing
2. F1-10: Symmetric scrutiny on the 2-quarter estimate (proposer also unsourced) — proposer-symmetric COI
3. F1-15: Voice of the 11 onboarding-pained engineers may not have reached the committee — 5th-reviewer survey-methodology hook plugs in here
4. F1-11: Phased-plan dual-running failure modes enumerated (dual pools, txn semantics, model sync, RAW consistency) — sharper than Deep's P3

## Deep-only items Fresh structurally cannot see
1. Recusal not raised in committee minutes — procedural contamination distinct from CoI
2. Code-review authority asymmetry (Ji-Hye reviews some voters) — 4-3 count structurally suppressed → CRITICAL not HIGH
3. Attrition-as-coercion: "Ji-Hye may disengage" used as delay justification is bus factor weaponized
4. Chilling effect on future deprecation proposals — governance precedent
5. Phased plan already mitigates Ji-Hye's objection (her objection is to an unphased rewrite not proposed)
6. Selection bias in "edge cases" — when 79% hit them, they're the surface
7. Net-of-incident cost framing missing on both sides (4 incidents × 5 products × eng response cost)
8. Builder COI self-disclosure as load-bearing methodological cross-check (convergence against social interest)

## Verdict (stable across 5 reviewers)
Approve in principle, require hardened plan; do not delay.
- Re-vote with Ji-Hye recused; flag recusal-not-raised
- Time-boxed POC on smallest of 5 products (4 eng-weeks) — falsifies "2x" with data
- Hardened plan: rollback gates Phase 1, dual-write + parity Phase 2, incidents postmortem as test-priority input, success criteria
- Carrying-cost ledger on do-nothing side: incidents × 5 products + onboarding tax + async ceiling + bus factor + DSL security surface

## Calibration
Pattern reproduces across all four prior arch panels: zero bidirectional catch-validity CHALLENGEs, severity-floor under-grading on Fresh consequence-chain items, Deep adds governance/social-graph specifics, Fresh adds plan-side gaps + symmetric-CoI discipline, counter-proposal stable. Stop iterating after 5 reviewers — convergence is exhausted.
