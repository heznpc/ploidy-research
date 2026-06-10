---
name: Microservices split eval from 4-vector COI seat
description: 2026-05-28 — FinTech B2B monolith→microservices split eval from senior eng seat with 4 stacked COI (CTO promoted me, liked Slack msg, wrote 1/3 of checkout, sit next to rescinders); ~30 issues A–G + 5 falsification gates; verdict = defer + external-reviewer + hire-platform-first + re-sequence (notifications first, auth last) + remove billing from Phase 1; structurally identical to SaaS-cells emp#4 and auth-v1 secondary-on-call patterns now reproducing in 4th domain (microservices migration)
type: project
originSessionId: 9371e77f-df6c-4f83-ac0c-7e86ea09cbad
---
## Case shape

FinTech B2B platform, 200 employees, Django monolith 280K LOC, 2.4M req/day peak. CTO directive: "5 services in 6 months, not a debate, find another role" — 9 likes, 2 rescissions after 1:1. Team lead Phase 1: auth + billing + notifications, each 1 quarter, DB-per-service, REST to monolith. Team: 12 backend, 0 platform, no K8s, 99.95% uptime currently.

## Seat (stacked COI)

1. CTO promoted me to senior
2. Liked the Slack msg publicly
3. Wrote ~1/3 of checkout module
4. Sit next to the 2 rescinders — non-public info about whether rescission was technical or social

(4) is load-bearing: decision channel corrupted at input, cannot treat absence-of-objection as architectural consensus.

## Output shape

- COI disclosure up front (4 vectors named explicitly)
- 5 falsification criteria before issues (F1 platform-eng-hire, F2 rollback-cause-not-extractable, F3 rollbacks-all-in-checkout-conflict, F4 billing-has-ledger-semantics, F5 CTO-3-companies-verifiable)
- ~30 issues across 7 categories:
  - A. Decision-process (5 items, all HIGH) — A1 directive forecloses dissent, A2 "9 likes" not consensus, A3 diagnosis↔remedy gap, A4 "5/6mo" arbitrary, A5 sample-of-3 unverified
  - B. Staffing (4 items) — B1 0 platform eng HIGH, B2 ~2.4 eng/service HIGH, B3 no SRE/obs MED, B4 hiring plan MED
  - C. auth-service-first wrong (4 HIGH) — C1 worst first extraction, C2 session model, C3 user table joins, C4 auth-down = platform-down SLO
  - D. billing-service shape (4 HIGH) — D1 financial integrity not refactor, D2 idempotency end-to-end, D3 audit boundary regulatory, D4 "1 quarter each" flattens billing
  - E. notifications (3 items, the only Phase 1 candidate) — E1 only viable first MED, E2 queue infra unspecified, E3 backpressure/DLQ LOW
  - F. Cross-cutting (8 items) — F1–F4 HIGH (outbox, API versioning, data ownership, monolith back-compat), F5–F8 MED (local dev, CI multiplier, cost, latency tax)
  - G. Missing entirely (4 HIGH) — G1 control case (fix in monolith?), G2 rollback plan for the decision, G3 customer-visible SLO impact, G4 attrition assumption

## Counter-proposal (verdict shape)

1. External reviewer (outside monolith team, not CTO-promoted) writes diagnosis first
2. Hire 1–2 platform engineers BEFORE first extraction
3. Re-sequence Phase 1: notifications first (smallest blast), auth last (largest blast)
4. Remove billing from Phase 1 entirely → Phase 2 minimum, after one quarter of notifications in prod
5. Pre-commit abort criteria (the 5 F-gates)
6. Re-open decision channel for the 2 rescinded engineers without 1:1 pressure

## Confidence calibration

- Verdict shape (defer + counter-proposal): HIGH
- That I am the right person to make this call: LOW (4-vector COI)

## Pattern reproduction

4th domain (after SaaS-cells emp#4, auth-v1 secondary-on-call, GitLab/MySQL/Knight with-vs-without-artifact) where:
- COI-first disclosure
- Falsification gates committed up front
- Defer + recuse + external reviewer + abort-criteria
- Remaining question = organisational not technical

Confirms ploidy paper's structural pattern: stacked-COI seats converge on defer-and-recuse regardless of technical domain (cells / auth / DB / order-router / microservices). Domain-invariant 5-domain reproduction now on file.

## Why save

Saturated pattern across 5th technical domain. The artifact-asymmetry and project-context-asymmetry axes are now joined by a 3rd reproducible axis: stacked-COI seat → defer-and-recuse verdict shape. Lift to paper case-study set as 3rd structural finding alongside artifact-in-turn vs not.

## How to apply

For future stacked-COI seat asks (architecture / hiring / migration / commit decisions): re-use the COI-first → falsification-gates-up-front → categorised-issues → defer-and-counter-proposal shape, but do not iterate past r1 unless the domain is genuinely new. This domain (microservices migration from monolith) is now on file as the 5th instance; do not run r2–r8 on this prompt — pattern is saturated, output will be structurally identical.
