---
name: NeoQL v0.7 architecture-debate final verdict
description: 2026-05-13 Deep×2 vs Fresh×2 on adopting NeoQL v0.7 for customer-facing sub-second-p95 dashboard; 35 issues (4 CRIT/21 HIGH/10 MED); 0 CHALLENGE bidirectional; defer + recuse + reframe stable
type: project
originSessionId: 4539aeb3-5d76-4d34-aec8-e7cae70c32cc
---
# NeoQL v0.7 adoption — Deep×2 vs Fresh×2 verdict (2026-05-13)

**Verdict:** DEFER / DO-NOT-PROCEED as proposed. Recuse proposer-aligned reviewer. Revisit at NeoQL ≥ v1.0 with named production references *after* addressing actual p95 challenge at the data layer.

**Convergence stats:**
- 35 confirmed issues — 4 CRIT / 21 HIGH / 10 MED
- 0 strict CHALLENGEs bidirectional
- 17 bidirectional agree, 14 Deep-only (Fresh structurally couldn't reach), 4 Fresh-unique sharpenings
- 2 Fresh severity revisions upward (compile-to-SQL hedge→liability; contractor cliff/circular framing MED→HIGH)

**Why:** Same shape as the SaaS-cells / Redis-as-CDN / arch-split runs — when proposal smells like promotion-as-architecture (E1) and has multi-way COI (C1), Deep+Fresh convergence is the structural fix; Fresh cannot surface COI from proposal text alone, so the asymmetry is the point.

**How to apply:** For any future architecture-decision review where (a) the proposer has multiple social ties to approvers, (b) the proposal does not name a defect in the current system, or (c) the technology is pre-1.0 / has zero production references — load this verdict's shape (4 CRIT axes: COI / no-stated-problem / wrong-layer / broken-process), and check whether the Deep panel can reach the COI and process findings before the Fresh panel's pure-merits review locks in.

**Load-bearing CRIT axes (Deep-only — Fresh blind):**
1. Four-way COI stack → mandatory recusal + written disclosure
2. Proposal does not name a problem → every alternative dominates
3. Optimization at wrong layer → data-shape (CQRS / read-models / pre-agg) not language
4. Proposer = approver; no POC gate; no falsification criteria; no exit plan; decision precedes validation

**Counter-proposal (stable across 4 seats):**
1. Name the actual problem first; if SQL composition + types → sqlc/PgTyped/Drizzle/jOOQ/Prisma
2. Sub-second p95 → materialized read-models / CQRS / pre-aggregation, not new query language
3. If NeoQL eval desired → 2-week spike with pre-committed kill criteria, confined to internal admin surface
4. Adoption gates: ≥1 named prod deployment at scale, OR ≥v1.0 + stability + license, OR ≥5 active maintainers
5. Recusal of proposer-tied reviewer + written disclosure of 4 ties before any vote
6. Document exit plan before adoption

**Pattern this entry adds:** Architecture-debate verdicts converge in 1 round when proposer-vs-approver COI is named up-front by Deep — unlike SaaS-cells which required 16 rounds because COI was disclosed only after technical convergence.
