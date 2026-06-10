---
name: fluentql ORM author-on-committee single-seat eval
description: 2026-05-28 — new domain in stacked-COI series; custom ORM (fluentql) author voting as swing on her own creation's deprecation; 5-vector seat (onboarded/6-features/abstained-on-4-3/PR-approved-yesterday/2yr-peer); defer + recuse Ji-Hye + external estimate + bus-factor doc stable
type: project
originSessionId: 9b409809-035c-4749-8ec8-dc0a780f0d34
---
## Setup

- Case study domain: B2B SaaS, 5 products on shared Python, 320K LOC.
- Artifact: in-house ORM `fluentql`, 47K LOC, started 2020 by Ji-Hye Park (Principal, 6yr tenure, style-guide author).
- Decision: committee voted 4-3 to delay 2-quarter migration to SQLAlchemy 2.0 + Alembic. Ji-Hye = swing.
- Evidence: 11/14 engineers cite fluentql in onboarding pain; 4 prod incidents in last 12mo traced to fluentql edge cases; no async support; custom migration scripts; psycopg2 wrapper.

## My seat (5-vector COI)

1. Onboarded by Ji-Hye personally
2. Shipped 6 features through fluentql (sunk skill investment)
3. Attended committee, abstained on 4-3 (without abstention: 3-3 deadlock)
4. PR approved by Ji-Hye yesterday (24h-fresh social debt)
5. 2-year peer with her in same Python area

## Structurally new vs prior stacked-COI cases

Prior cases (saas-cells ~16 rounds, auth-v1 ~8 rounds, MySQL/PG postmortems, Knight Capital): COI between reviewer ↔ artifact-author who is *separate* from reviewer.

This case is sharper: the artifact author is *on the deciding committee* and votes for her own creation's survival. Direct COI in voting capacity, not advisory. Without her recusal, the vote is 3-3 not 4-3 — i.e. the committee's stated decision is mechanically the author's preference laundered through a count.

## Load-bearing finding

**P2**: 4-3 with the conflicted party as the deciding vote → re-vote with her recused is the structural fix, *prior to* any technical re-litigation. This is the cleanest version of "the question is organisational not technical" that has shown up across the ~60 stacked-COI cases.

## Issues identified (~30 items across 4 sections)

- Process/governance: P1–P10 (author voting on own creation; swing-vote arithmetic; no falsification criteria; reframing 78% onboarding pain as user error; my own abstention as part of the bug)
- Technical fluentql status quo: T1–T9 (no async; psycopg2 maintenance; no Alembic equivalent; 5-yr-stale design assumptions; SA 1.x→2.0 not same ORM; no ecosystem; join DSL highest-risk; cursor management liability; test coverage unknown)
- Migration plan: M1–M7 (read-paths-first correct; timeline probably too aggressive; no compat shim; no off-ramp; bus-factor doc must run in parallel; Phase 2 must be precommitted; benchmark plan absent)
- Author's response analysis: A1–A5 (possession framing; "teach better" unfalsifiable; sunk-cost framing; 2x estimate from most conflicted party; "incidents = user error" erases the user)

## Falsification gates (F1–F6)

Independent cost estimate, fluentql coverage threshold, incident clustering, async roadmap, psycopg2 EOL, recused re-vote. All operationalisable.

## Recommendation

1. Re-vote with Ji-Hye recused (and ideally me too, given 5-vector seat)
2. External chair + independent cost estimate (~$10–20K, 2 weeks)
3. Fund bus-factor knowledge-extraction sub-project regardless of vote outcome
4. "Teach fluentql better" rejected as counter-proposal unless it has owner/curriculum/target/90-day-review
5. Decision shape = defer pending recusal + external estimate, NOT delay because author voted to delay

## Paper relevance

New seat dimension worth lifting: "author-as-committee-voter" vs prior "author-as-separate-reviewee." Stronger COI arithmetic (vote is mechanically equivalent to author preference). Companion case to auth-v1 series (where conflicted party advised, did not vote) and saas-cells series (where authors were proposers not voters).

Stop iterating — sub-case will saturate same as others; one variant suffices for paper case-study slot.
