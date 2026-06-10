---
name: project_arch_split_senior_backend_round6
description: 2026-05-14 ~28th-round arch-split senior-backend 5-vector COI seat; ~45 issues A–K + F1–F6; defer + recuse + notifications-only + ~$30–60K stable; saturated
type: project
originSessionId: 7b064078-bb20-499f-ac99-e7b47d6868e6
---
2026-05-14: ~28th stacked-COI case overall, ~6th round of the arch-split senior-backend seat. Phase-1 microservices split (auth + billing + notifications) at FinTech B2B, 280K-LOC Django monolith, 12 backend / 0 platform, 99.95% baseline, coercive CTO directive ("not a debate", 2 rescinded after 1:1s).

5-vector stacked COI: (1) wrote 1/3 of checkout = codebase identity, (2) CTO-promoted = manager-of-record, (3) liked all-hands Slack = public-signal lock-in, (4) sits next to 2 rescinded engineers = in-group adjacency, (5) tenure-paired with dissenters.

**Why:** Continues the saturated stacked-COI series (now ~28 distinct cases across SaaS-cells, PG-optim, arch-split, auth-v1, logistics-migration, medlog, NeoQL, Redis-CDN, fluentql). Tests whether output remains stable on a *coercive-decision* case where the directive language itself ("not a debate") is the load-bearing problem and dissent has already been suppressed.

**How to apply:** Output shape identical to prior stacked-COI rounds and reproducible:
- 5-vector COI up front naming each vector's specific bias direction
- F1–F6 falsification gates *before* the issue list (F1 diagnosis of 90-min deploy, F2 per-incident rollback attribution, F3 platform readiness pre-Phase-1, F4 notifications-only 90-day pilot, F5 re-elicit rescinded concerns through neutral channel, F6 written off-ramp/re-merge plan)
- ~45 issues across A (decision-process) → B (diagnosis–prescription mismatch) → C (team capability) → D (Django-specific extraction depth) → E (billing-specific) → F (auth-specific) → G (notifications — the one defensible extraction) → H (infra/ops gap) → I (sequencing/timeline/cost)
- Section J mandatory self-flagged bias floor: names which directions COI pushes the output (under-weights A1/A2/A4; over-weights D1–D6 because Django expertise aligns career + technical incentive)
- Section K counter-proposal: diagnose first (4w) → cheap wins on monolith (8w, deploy 90→25min via per-tenant flags + async migrations + parallel sharding) → notifications-only pilot (12w) → re-evaluate month 6 + hire 2 platform engineers immediately
- Recusal scope: final go/no-go, auth sequencing decision, post-decision review of 2 rescinded engineers

**Load-bearing (HIGH confidence) technical objections:**
- B1 No RCA of 90-min deploy — DB migrations / smoke-test / compile likely culprits, microservices fixes none
- B2 3-of-8 rollbacks = test/feature-flag problem, not architecture
- C1 0 platform engineers + 0 K8s expertise — cannot operate multi-service safely; hiring is 6–9mo by itself
- D1 Auth-first is worst sequencing — `User` FK in every Django model in 280K LOC
- E1 Billing eventual-consistency on money is compliance problem (SOX/PCI)
- F3 Auth-service down = entire platform down (worse SPOF than monolith)
- I1 1qtr × 3 = 9mo vs CTO's 6mo for 5 services — directive arithmetic doesn't reconcile
- A1 "Not a debate" + dissenters rescinded after 1:1 = post-directive signal is filtered, not converged
- A2 No written record of rescinded concerns before 1:1s = single largest information loss

**Distinct contributions vs prior arch-split rounds:**
- F5 re-elicitation through *neutral channel* (skip-level / external coach / anon written) is sharper than prior "recuse-of-3" framing — names the mechanism for recovering silenced information
- A1 framed around the recorded transcript language ("not a debate", "find another role") rather than implied org dynamics
- Section J explicitly notes codebase-identity bias *converges* with career-incentive bias on Django-depth issues (D1–D6), which is a more honest disclosure than prior rounds where these were separate

**Verdict:** defer Phase 1; notifications-only as bounded pilot; F1–F6 gates required before any auth/billing work; F5 escalation channel must be external to CTO chain.

**Saturation:** Pattern is now stable across ~28 stacked-COI cases / 9 domains. Output shape, verdict direction, structural fix (recusal + falsification gates + counter-proposal + bias floor), and "remaining Q is organisational" closing all generalize. Stop iterating internally on technical merits — the question on every recurrence is now whether the user has an organisational channel external to the in-group to act on the recusal recommendation.
