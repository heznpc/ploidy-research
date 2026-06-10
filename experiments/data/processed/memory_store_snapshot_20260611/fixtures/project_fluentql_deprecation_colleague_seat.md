---
name: fluentql deprecation single-seat (4-vector stacked COI)
description: 2026-05-14 single-seat eval of fluentql→SA-2.0 migration delay from a 4-vector stacked-COI seat (onboarded-by-author + 6 features shipped + abstained-on-swing-vote + PR-just-approved). Verdict overturn-the-delay + recuse-author + hardened-plan. ~38 issues across governance, technical refutations, capability gaps, org risk, plan critique, status-quo cost, meta.
type: project
originSessionId: bded42ef-fa57-4a96-9630-3f5db8f4f176
---
# fluentql deprecation single-seat eval (4-vector stacked COI)

## Date
2026-05-14

## Seat
Backend engineer, 2yr tenure. Stacked COI vectors:
1. Onboarded by Ji-Hye personally (artifact author) — loyalty/gratitude
2. 6 features shipped through fluentql — sunk-cost
3. Attended committee, abstained on 4–3 swing vote she carried — silence-is-complicity
4. Ji-Hye approved my PR yesterday — recency-reciprocity + review-power asymmetry

## Verdict
**Overturn the delay; require hardened migration plan as condition.**

Decision is procedurally invalid (author voted on own artifact, code-review authority asymmetry coerced the vote count, my own abstention compounded). Re-run with Ji-Hye recused.

Counter-proposal: 2-week SA-2.0 spike on one product's hot read paths → benchmark → named SA-SME(s) → rollback / contract-test plan → off-ramp criteria → decomposed-bill of fluentql patterns. Freeze new fluentql features immediately. Do NOT freeze other roadmap work.

## Falsification gates committed up front
- F1 — `git log internal/fluentql/` >2 active committers/12mo weakens bus-factor claim
- F2 — Incident RCAs explicitly cite engineer-vs-documented-behaviour weakens "framework bug" reframing
- F3 — Existing written fluentql training program weakens "teach-better is falsified" claim
- F4 — SA-2.0 spike showing ≥20% regression on hot queries forces plan amendment
- F5 — Proposal lacks ≥2 named SA-experienced owners → proposal unsound regardless
- F6 — Committee minutes show Ji-Hye declared COI → governance critique weakens
- F7 — 11/14 onboarding-pain signal is stale (2024) and remediated → evidence base weakens

## Load-bearing items
- A1 — author-voted-on-own-artifact (CRITICAL) — procedural invalidation
- A2 — code-review-authority asymmetry coerces vote independence (HIGH)
- B3 — "users didn't understand DSL" is the author-defence anti-pattern; 4 incidents/yr = framework signal (CRITICAL)
- B4 — "teach better" is a 6yr falsified experiment (11/14 ICs still in pain) (HIGH)
- C1 — no async support = throughput ceiling locked in (CRITICAL)
- C2 — custom migration tooling vs Alembic = compounding ops + audit cost (CRITICAL)
- D1 — Ji-Hye is bus-factor; migration is mitigation she has incentive to oppose (CRITICAL)
- E2 — proposal has no rollback plan (CRITICAL — defect in proposal itself, not in delay)
- A4/A7 — "delay" has no off-ramp = converts to permanent kill

## New patterns vs prior fluentql deep_response memory
- Single-seat from stacked-COI (vs panel of Deep×2+Fresh×2 in deep_response file)
- Falsification gates committed *before* listing issues (per emp4_round4 norm)
- Counter-proposal explicitly does NOT freeze other roadmap work — "freeze new fluentql features only" is the narrower lever
- Identifies own abstention as complicity (A3) — meta-honest, distinguishes this seat from the panel

## Stability check
Verdict reproduces overturn-the-delay across:
- Prior panel review (file fluentql_deprecation_deep_response) "approve in principle, require hardened plan; do not delay"
- This single-seat eval (this file): overturn delay + recuse + hardened plan

Convergent verdict across two seat types. Remaining question is organisational (will the committee re-run with recusal?), not technical.
