---
name: fluentql → SQLAlchemy migration delay — 5-vector COI seat eval
description: ~34th stacked-COI case; mentee + 2yr coworker + recent PR approval + identity-coded codebase + abstained-on-swing-vote evaluating fluentql vs SQLAlchemy 2.0
type: project
originSessionId: c031f35f-5dde-4db3-ad09-40f479eeeea7
---
2026-05-14: B2B SaaS, 47K LOC custom ORM (fluentql) by Ji-Hye Park (principal eng, framework author, style-guide author). Committee voted 4-3 to delay migration to SQLAlchemy 2.0 + Alembic; Ji-Hye was the swing.

**Seat COI (5-vector):** mentee + 2yr coworker + PR approved yesterday + 6 features shipped *in* fluentql + abstained on the very vote.

**Why:** This is now the ~34th stacked-COI case across 7 domains (saas-cells, pg-optim, medlog, auth-v1, logistics-migration, cdn-redis, fluentql). Output shape stable:
- 5-vector COI declared up front
- 6 falsification gates (F1–F6) committed before issue list
- ~30–40 issues across A–E categories (governance / technical / migration-plan-flaws / sociotech / author-bias)
- Verdict: migrate-but-recuse-authors + diagnose-first + external review (channel external to in-group) + spike-to-validate + counter-proposal
- Remaining question is organisational not technical

**How to apply:** For future stacked-COI architecture evals, produce in same shape directly; pattern is fully saturated. Skip Ploidy debate iteration — calibration is "stop iterating internally, escalate to external channel."

**Domain-specific load-bearing catches for fluentql case:**
- A1: framework-author-as-swing-voter is the cleanest COI in any case so far
- A6: 4-3 with ≥2/7 conflicted has no clean majority signal
- B5: Ji-Hye's *"I know exactly which corners we cut"* is the failure mode, not reassurance — key-person risk explicit in her own words
- C1: "reads then writes" is wrong axis; strangler-fig by module is right axis
- E3: comparing 5-year-old SQLAlchemy 1.x to fluentql is irrelevant; 2.0 is the comparison
- D1: 79% onboarding-pain = structural, not pedagogical (pending F1 verification of slack thread)
