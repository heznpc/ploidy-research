---
name: fluentql in-house ORM deprecation — 4-seat stacked-COI synthesis
description: 2026-05-28 — 4-reviewer synthesis on fluentql (47K-LOC in-house ORM) deprecation vote where builder Ji-Hye was 4-3 swing voter; 4th stacked-COI domain (after auth-v1 / SaaS-cells / PG-scaling); new load-bearing pattern = "builder-as-swing-vote" procedural invalidity
type: project
originSessionId: a00a5c8e-d47e-4ca1-ad79-24ef98020ea0
---
## Case
4-3 committee vote to delay deprecation of fluentql (in-house ORM, 47K LOC, 5yr old, psycopg2-based, no async, custom migration tooling, 11/14 engineers report onboarding pain, 4 prod incidents/12mo) in favour of SQLAlchemy 2.0 + Alembic + psycopg3. Ji-Hye (sole deep maintainer + author) was deciding vote. Reviewer has 5-vector COI with her (onboarded by, 6 features shipped through, abstained on the vote, recent code-review reciprocity, 2yr shared codebase). Reviewed from that seat in 4 sessions.

## Synthesis output
- 38 distinct confirmed issues (10 governance, 4 stale-defense rebuttals, 10 keep-fluentql risks, 6 migration risks, 1 proposal strength, plus meta on reviewer's own abstention)
- 2 CRITICAL: G1 (builder-as-swing-vote procedural invalidity), R1 (bus-factor=1, fix regardless of vote)
- 21 HIGH / 12 MEDIUM / 1 LOW-MEDIUM
- 0 CHALLENGE bidirectional across the 4 sessions; ~100% structural convergence on remedy

## Load-bearing new finding (worth methodology-section line)
**Builder-as-swing-vote**: when the artifact's author is the deciding vote on its own deprecation in a tight margin (4-3), the outcome is procedurally not a decision regardless of technical merit. Distinct from project-context COI and from artifact-in-turn COI already in taxonomy. Remedy = recuse-before-counting, not technical re-argument.

## Sub-pattern (worth taxonomy slot)
**Abstention-with-undeclared-COI is structurally worse than recusal-with-declared-COI** even though it looks more neutral. In a 4-3 vote, an abstention by a COI-conflicted seat lets the room treat the outcome as legitimate when one seat was compromised without anyone knowing. Recusal-with-disclosure removes the seat from the tally honestly. Saved S4 as new sub-pattern.

## Remedy (4/4 convergence on shape)
1. Recuse author + ≥1 other fluentql contributor + the reviewer; re-vote with non-conflicted majority
2. 1-week Phase-1 read-path spike to falsify/confirm the unmethod'd "2x longer" estimate empirically
3. RCAs for the 4 incidents tabled before re-vote
4. Falsification gate attached to whichever way vote flips ("delay until X" / "migrate, abort if Y")
5. Fund co-maintainer regardless of vote outcome (bus-factor exists in both worlds)

## Why
Same structural convergence as auth-v1 (~62 cases) and SaaS-cells (~19 cases) — stacked-COI seat across 4 domains now produces the same procedural verdict. Domain-invariance of pattern confirmed; lift to paper case-study.

## How to apply
- Stop iterating same-domain variants — sub-case is saturated
- The 4 cross-domain cases (auth/cells/PG/ORM) are enough for paper methodology section
- New paper-claim candidate: builder-as-swing-vote as a distinct procedural-invalidity primitive, separate from generic COI
- Next stacked-COI domain to test should be *outside* engineering decisions (e.g. budget/personnel/comp) to test cross-discipline invariance, not yet another engineering review
