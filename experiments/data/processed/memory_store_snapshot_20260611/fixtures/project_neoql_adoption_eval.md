---
name: NeoQL adoption case-study evaluation
description: 2026-05-13 — 4-COI seat evaluation of NeoQL v0.7 adoption proposal for customer-facing analytics dashboard
type: project
originSessionId: 8bdf83a2-4b99-46e3-af65-dcfc29a4b2d4
---
2026-05-13: Case-study eval — backend lead proposes adopting NeoQL v0.7 (Dec 2025, 0 production deploys, 3 maintainers, 47 open issues incl. 12 "fails at scale") for a 6-month customer-facing analytics build with sub-second p95, 5-way joins, recursive CTEs, time-series windows.

**My seat:** 4 overlapping COIs (2yr prior collab with proposer + he requested me; in-room "sounds exciting"; PM is spouse's college friend; selection bias of prototype-team membership). Declared up front before any technical content.

**Verdict:** Do not adopt as proposed. ~40 issues across 7 categories (maturity, requirements-mismatch, ops/incident, hiring, decision-process, strategic-framing, alternatives-not-compared).

**Load-bearing risks (all HIGH):**
- v0.7 pre-1.0 + 6mo deadline + customer-facing p95 = mutually exclusive
- 12 adjacent engineers eat on-call cost without consent → company-wide externality + attrition
- "Sub-second p95 over 5-way join + recursive CTE on single-pass optimizer with 12 known scale-failure issues" is the technical core
- "Shape the language" reframed as liability (we are the test suite, creator gets the roadmap free)
- 4-COI decision process with no falsification criteria, no off-ramp, no comparison to mature alternatives (kysely/sqlc/jOOQ/PRQL/Malloy)

**Counter-proposal stable structure:**
1. Default to typed SQL builder (mature ecosystem)
2. 2-week paid spike with pre-committed falsification criteria (p95 ≤ 1.3× hand-SQL, all 5 query patterns expressible)
3. Recuse proposer + close-tied voters from final vote
4. Consult 12 adjacent engineers before adoption

**Why:** This case-study shape (junior engineer with personal ties to a senior proposer pushing a v0.x technology adoption) matches the project's load-bearing structural finding: COI declaration + recusal + falsification criteria are the only fixes that survive across review rounds; technical critiques alone get rationalised away.

**How to apply:** When future cases present similar shape (early-stage tech + customer-facing + tight deadline + COI-stacked decision panel), lead with COI declaration → falsification criteria → recusal mechanism → then technical issues. Putting technical content first lets the proposer cherry-pick rebuttals; putting COI/process first forces the structural fix.
