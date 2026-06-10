---
name: fluentql ORM migration delay — stacked-COI seat
description: 2026-05-28 — backend engineer seat (onboarded by Ji-Hye, 6 features shipped through fluentql, abstained 4-3 vote where she was swing, she approved my code review yesterday) evaluating 47K-LOC custom-ORM → SQLAlchemy 2.0+Alembic migration delay. ~14 issues P1–P4 + T1–T9 + F1–F5 gates. Builder-as-swing-vote is load-bearing finding. First non-DB-incident-review domain in stacked-COI series.
type: project
originSessionId: fbb69077-713f-4569-a74a-90afcf1a44e9
---
2026-05-28: 9th meta-case domain for paper case-study series — *build-vs-buy / custom-ORM deprecation* under stacked-COI seat. Distinct from prior auth-v1 (security migration) and SaaS-cells (greenfield architecture) cases.

**COI vectors (4):** onboarded by proponent of status quo, 6 features through her artifact, recent code review approved by her yesterday (current reciprocity), attended committee + abstained on 4-3 vote where she was the swing.

**Load-bearing structural finding (new):** *builder-as-swing-vote* is procedurally non-decidable, regardless of technical merit. Has to be re-run with builder recused before any technical content is dispositive. This is sharper than the prior "recuse-of-3" pattern in SaaS-cells because it is a single-actor pivot, not a co-author cohort.

**Issues delivered (~14):**
- P1–P4 process/governance (builder=swing HIGH, non-falsifiable defenses HIGH, no gates HIGH, style-guide-authorship venue MEDIUM)
- T1–T9 technical (psycopg2/no-async HIGH, 4 incidents in 12mo HIGH, bus factor HIGH, custom migration tooling cost HIGH, onboarding cost MEDIUM-HIGH, dated SQLAlchemy-1.x rebuttal HIGH, strangler-fig stall MEDIUM, no prior-art benchmark MEDIUM, shared-codebase blast radius MEDIUM)
- F1–F5 falsification gates (spike, labelled post-mortems by non-author, async-blocker ticket count, measured onboarding-week cost, re-vote with builder recused)

**Why-loaded:** the builder's quoted defense ("incidents were team not understanding the DSL", "I know which corners we cut", "2x longer than estimated") is non-falsifiable as written. Each clause has a structural counter:
- "users don't understand" → if 11/14 cite it, that IS the framework problem
- "I know corners" → that is a bus factor *for* migration, not against
- "2x longer" → asserted without counter-estimate

**Apply to:** future build-vs-buy seats where the artifact author is on the deciding committee. The procedural fix (builder-recuses, then re-vote) precedes any technical re-evaluation. Do not engage on technical substance until the process gate is closed; otherwise the technical answer is unfalsifiable by construction.

**Saturation note:** single-pass. Do not iterate; the seat is structurally similar to auth-v1 r1 (single-vector → multi-vector COI builder seat) but in a new domain. If a second pass is requested, expect it to converge to the same P1+T1+T3 load-bearing finding — lift to paper rather than re-running.
