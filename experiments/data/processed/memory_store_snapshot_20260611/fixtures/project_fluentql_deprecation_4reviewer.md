---
name: fluentql deprecation 4-reviewer synthesis
description: 2026-05-14 4-reviewer (all conflicted seats) synthesis of the fluentql-vs-SQLAlchemy-2.0 delay-decision; 2 CRIT (author-swing-vote, bus-factor-1), 16 unanimous HIGH, defer-invalidation stable
type: project
originSessionId: c930e1e8-5690-4d36-be6b-330f752aebbc
---
# fluentql deprecation 4-reviewer synthesis (2026-05-14)

4 reviewers, all 5-vector-COI seats (mentored by Ji-Hye, shipped through fluentql, abstained on swung vote, fresh reciprocity from her code review), evaluated the architecture committee's 4-3 delay decision on migrating off the 47K-LOC in-house ORM.

## Convergence
- 0 CHALLENGE bidirectional across all 4 seats.
- All 4 self-recused; net bias direction = toward delay → convergence on "delay was wrong" is bias-corrected stronger.

## Load-bearing findings (CRITICAL)
- **A1**: author-as-swing-vote on deprecation of own artifact — Ji-Hye built fluentql + cast the deciding vote. Textbook CoI. 4/4 unanimous.
- **C2**: bus-factor-of-1 on 47K LOC custom ORM — monotonically increasing risk; committee just voted to deepen it.

## Unanimous HIGH (16 items)
A2 no-COI-disclosure, A3 no-exit-criteria-for-delay, A4 4-3-collapses-on-recusal, A5 power-concentration, A6 stacked-CoI-committee, B1 SA-1.x-anchoring, B2 blame-the-user, B3 authority-as-evidence, B4 2x-estimate-no-methodology, B5 teach-better-already-failed-5yr, C1 no-async, C3 no-Alembic, C4 1-incident-per-quarter, C5 78%-onboarding-pain, C6 psycopg2-maintenance-only, D1 2-quarter-estimate-optimistic, D2 dual-run-coordination-missing.

## Majority HIGH (7)
B6 47K-LOC-sunk-cost, C10 style-guide-cultural-lock-in, D3 no-spike-before-vote, D4 no-parity-tests, D5 no-abort-criteria, E1 delay-asymmetry-compounds, E2 process-is-the-defect, E3 working-code-is-frozen-judgement.

## Counter-proposal (4/4 stable)
1. Vacate the 4-3; recuse Ji-Hye + proposer + everyone she onboarded.
2. 2-week spike, one read-heavy endpoint, real estimate + parity findings + rollback design.
3. Falsification gates attached to re-vote ("if N more incidents in 6mo → migrate regardless").
4. Document Ji-Hye's mental model independent of decision — bus-factor mitigation is non-optional.
5. Anonymous engineer survey on top-3 friction sources.

## Calibration
Remaining question is organisational, not technical. The technical case is decided; the structural lock-in (style-guide + ORM + swing vote all in one node) is what produced the wrong outcome. Stop iterating panel-internal; the next move is procedural recusal external to the conflicted committee.

## How to apply
When the user asks about: ORM migration decisions, deprecation of artifacts authored by deciding voters, committee-CoI patterns, "delay" without exit criteria, bus-factor-of-1 on home-grown frameworks — reference this synthesis. Pattern matches the architecture-debate series (saas_cells, arch_split, redis_cdn): defer-or-don't decisions where structural CoI on the swing vote produced procedurally invalid outcomes.
