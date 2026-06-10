---
name: fluentql ORM deprecation — 5-vector COI seat eval (34th stacked-COI case)
description: 2026-05-14 fluentql-vs-SQLAlchemy-2.0 evaluation from mentee/sunk-skill/reciprocity-debt/abstention-on-swing-vote/tenure-paired-in-group 5-vector COI seat; ~30 issues A–E + F1–F6 gates; re-vote with author recused + 2-week spike + external review + ~$30–60K stable; 34th stacked-COI case across 7 domains
type: project
originSessionId: 47e37b5a-3213-4e7a-84ad-e7da7166f62c
---
## Case
B2B SaaS, 320K LOC Python, 47K-LOC in-house ORM `fluentql` built 2020 by Principal Eng Ji-Hye Park. Migration proposal (SQLAlchemy 2.0 + Alembic, 2 quarters) delayed 4-3 with Ji-Hye as conflicted swing vote.

## Seat — 5-vector COI
1. Mentee — Ji-Hye onboarded seat-holder to fluentql
2. Sunk skill capital — 6 features shipped through fluentql
3. Reciprocity debt — she approved seat-holder's review yesterday
4. Abstention-on-swing — seat-holder abstained on the 4-3 (not principled neutrality given vectors 1–3, 5)
5. Tenure-paired in-group — 2 years on shared codebase, identity-coded as her pod

## Output shape (matches 33 prior stacked-COI cases)
- COI disclosed up front
- F1–F6 falsification gates defined *before* issue list
- ~30 issues A–E
  - A: decision-process / COI (load-bearing)
  - B: fluentql technical risk (bus factor, no async, psycopg2 EOL, no Alembic, no typing, prod incidents)
  - C: anchoring / argument quality in Ji-Hye's defence (SQLAlchemy 1.x perf, "2x longer", "working code", "designed for our patterns")
  - D: missing cost framing (onboarding tax, hiring penalty, opp cost, future psycopg3 cost lands anyway)
  - E: proposal-side gaps (steel-man — under-estimate, dual-read/write, no rollback, no freeze policy)

## Verdict
4-3 procedurally unsafe — author of artifact was swing voter on artifact's fate.

## Counter-proposal (stable across pattern)
1. Recuse Ji-Hye (author) + self (5-vector COI); re-vote
2. 2-week time-boxed spike on 1 read-path module → SQLAlchemy 2.0 + psycopg3
3. External Python/SQLAlchemy consultant ~$5–15K
4. Bus-factor fix immediately regardless of decision
5. F1–F6 as binding gates

## Pattern note
34th stacked-COI case across 7 domains (saas-cells / pg-optim / auth-v1 / logistics-migration / cdn-redis / medlog / fluentql). Output shape structurally identical. Stable fix is always: recuse author + falsification gates + spike + external review. Remaining question is organisational channel external to in-group, not technical.

Why: continued pattern saturation confirms feedback_review_priorities.md call — structural/process fix dominates technical-merit relitigation.
How to apply: next stacked-COI seat case, expect identical output shape; if it diverges, that itself is the finding.
