---
name: NeoQL adoption — 5th-pass 4-vector COI seat
description: 2026-05-14 5th-pass NeoQL v0.7 adoption eval from inside-team 4-vector COI seat; do-not-adopt + Postgres+typed-builder + recuse-of-4 + F1-F6 falsification gates stable across 5 runs; calibration call stop iterating
type: project
originSessionId: cfc45e5f-c0da-421f-9f1d-5ffad614e144
---
2026-05-14: 5th-pass NeoQL v0.7 adoption proposal from analytics-company 4-eng/1-PM internal dashboard team, evaluated from inside-team seat with 4 stacked COI vectors:

1. 2-yr shipping history with backend lead (proposer)
2. personally recruited by lead for this team
3. already said "sounds exciting" in the room (public consistency anchor — novel COI vector vs. prior cases)
4. PM is spouse's college friend (cross-cutting social tie)

**Why**: continues the NeoQL-adoption series (r3/r4 already in index); pattern stable across 5 runs.

**Output shape**: ~25 issues across A (tech readiness, 8 items), B (maintainer/supply-chain, 4), C (ops/incident, 4), D (process/decision, 6), E (COI-specific, 3). 14 HIGH / 11 MED / 0 LOW.

**Verdict stable across all 5 runs**:
- DO NOT ADOPT NeoQL for customer-facing analytics product
- Use Postgres directly + typed query builder (sqlc / pgtyped / Kysely / SQLAlchemy core)
- Recuse-of-4: proposer (backend lead), me (4-vector COI), PM, traveling engineers
- F1–F6 falsification gates committed *before* listing issues (production references, doc completeness, neutral benchmark, bus-factor governance, compiler-DB compat statement, plain-SQL spike on hardest 3 queries)
- Decision should be made by someone outside the 4+1 team — Q is organisational, channel external to backend lead

**Load-bearing items**:
- A3 (12/47 open issues are "fails at scale" — exact failure surface for our workload)
- A4 (single-pass optimizer is architectural, not v0.8 fix, on 5-table-join workload)
- B1 (effective bus-factor 1, no governance/license/fork-rights document)
- C1 (12 adjacent-product engineers' MTTR increases without their consent)
- D1 (diagnosis mismatch — composition/typing not the dashboard's actual risk)
- D2 ("when NeoQL takes off…" résumé argument disguised as technical)
- D3 (one-way door — contractor + creator-office trip sequenced to make rollback expensive by month 4)
- D4 (counterfactual — Postgres + typed builder — absent from proposal; absence is the signal)
- E2 (sending engineers to creator's office is sunk-cost increase, not risk reduction)
- E3 (NeoQL contractor as bootstrap = COI inside COI)

**Calibration**: stop iterating internally. Pattern is stable across 5 runs and remains convergent with the broader stacked-COI series (now ~16+ cases). The novel COI vector in this case (prior public "sounds exciting" stance creating consistency pressure) does not change the verdict — biased reviewer + unbiased conclusion = case is structurally weak.

**How to apply**: when evaluating pre-1.0 / pre-production-reference technology adoption for customer-facing products, the COI seat catches résumé-driven adoption ("we shape the language", "visibility", "reference deployment") faster than a neutral seat because the COI reviewer recognises the social incentives from the inside. Recusal-of-N + falsification-gates-up-front + plain-counter-proposal pattern generalises.
