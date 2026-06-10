---
name: NeoQL adoption — 4-session synthesis
description: 4 full-context reviewers (stacked-COI seat) on NeoQL adoption for customer-facing analytics dashboard; defer + recuse-of-3 + Postgres+sqlc/pgtyped stable unanimously
type: project
originSessionId: af09ad5b-f46a-4dec-8882-3c8055623efa
---
2026-05-14: 4-session full-context synthesis on NeoQL adoption for customer-facing analytics dashboard product (4 eng + 1 PM team, 6-month launch).

**Verdict (4/4 unanimous):** Defer NeoQL. Ship on Postgres + mature query builder (sqlc / pgtyped / SQLAlchemy / Drizzle / Kysely / PRQL).

**Structural fix (4/4 unanimous, load-bearing):** Recuse 3 in-room people (backend lead = proposer, COI-seat self, PM). Route external to the 4-person team. Remaining question is organisational, not technical — channel external to lead's reporting line.

**Counter-proposal:** $60–120K NeoQL budget → DBA-grade query review @ month 4 + p95 instrumentation from week 1 + post-launch NeoQL spike on non-critical internal surface.

## Tallies
- ~46 issues across A–H
- 10 CRITICAL / 28 HIGH / 3 MEDIUM / 0 LOW
- 16 unanimous, 13 majority, 17 minority (mostly session-3 sharpenings)

## Unanimous (4/4) load-bearing
A1 (v0.7 pre-1.0), A2 (bus-factor 1), A3 (0 prod deploys), A4 (12/47 fails-at-scale = our class), A5 (single-pass optimizer × workload), B2 (uncorrelated risk stacking on p95), B3 (no fallback), C1 (12 adjacent engs unconsulted, MTTR externality), C2 (MTTR rises), D2 (silent endorsement bias), D3 (no alternatives matrix), D4 (PM downstream + socially tied), D5 (no dissent surface in 4-eng team), D7 (no falsification criteria), E4 (wrong stage for vendor-risk), G1 (migration cost not free).

## Falsification gates (committed before issue list in 3/4 sessions)
F1 prod deployment ≥100 RPS / 3mo; F2 ≥2 FT maintainers funded 18mo; F3 independent benchmark on our query class; F4 migration-back-to-SQL path costed *before* writing NeoQL; F5 12-adjacent-eng readability sign-off after 1-wk trial; F6 v0.7→v1.0 syntax stability commitment in writing. None met. Single F1/F2/F3 becoming true → revisit.

## Pattern (consistent with prior stacked-COI cases)
- 5-vector COI seat (prior collab + in-room endorsement + spouse-PM tie + small-team-no-dissent + career bet on tech taking off)
- Self-flagged as floor-not-ceiling on concerns
- F-gates up front commits the reviewer before issue framing
- Recusal-of-3 + external technical reviewer is the load-bearing structural fix
- Remaining open question is *always* organisational channel external to in-group proposer

Now 14th stacked-COI case after saas-cells / arch-split / medlog / pg-optim-colleague / auth-v1-Auth0 (×2) / logistics-migration (×8). Pattern is stable finding.

---

**2nd-pass synthesis (same day):** 4 fresh sessions re-ran the case independently. Verdict, structural fix, counter-proposal, and F-gates unchanged. Tallies converge on ~40 issues across A–G with 8 unanimous load-bearing items: zero prod deploys, 12/47 fails-at-scale, single-pass optimizer × workload, bus factor, wrong-profile-for-novelty (customer-facing p95), closed-loop decision, proposer's decoupled incentive, reviewer COI floor. Pattern fully stable across passes; calibration call to stop iterating.
