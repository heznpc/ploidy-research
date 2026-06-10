---
name: NeoQL adoption final verdict
description: NeoQL pre-1.0 query language adoption for customer-facing analytics dashboard — Deep×2 + Fresh×2 final verdict; defer/do-not-adopt; stable across 2 rounds (2026-05-13, 2026-05-14)
type: project
originSessionId: 5eb85256-a549-490a-bffe-48728f13e7f4
---

## Round 3 (2026-05-14, later)
3rd Deep×2→Fresh×2 cross-review on NeoQL. 0 strict CHALLENGEs bidirectional sustained. 2 Fresh-side severity-floor errors flagged (F1-15 security LOW→MED given templated user input on dashboard surface; F2-12 mature-alternatives LOW→HIGH — primary rebuttal to pitch, not footnote). 14 Deep-only items reproduced: stacked decision-body COI (D5 load-bearing), decision-process unspecified, creator-relationship-as-criticism-silencer, license-as-fork-blocker chain (A8→A2), planner-stats-tuned-to-human-SQL, RLS/auth interaction, compiler-runtime-vs-buildtime ambiguity, recursive-CTE base-rate-hardness, generated-SQL-stability-across-minor-versions, customer-facing-as-wrong-pilot-venue principle, cross-panel-pattern-recognition. Two cleanest Fresh framings adopted: F1-2 "compiling to SQL doesn't save you" + F1-10 "unpaid contributor work on the critical path." Verdict + counter-proposal stable across 3 rounds.

## Round 2 (2026-05-14)
Re-run Deep×2 + Fresh×2 + bidirectional cross-review independently reproduced the same verdict: **48 issues (10 CRIT / 22 HIGH / 15 MED / 1 LOW)**. 0 strict CHALLENGEs across 35+ cross-reviewed points — highest convergence in the series. Counter-proposal (spike with falsification thresholds 1.3×/2×/5min, recuse proposer+conflicted reviewer, SLO-owner countersignature, internal-surface-first if passes) stable across rounds. 3 Fresh-unique catches: Rust-compiler skill bar, AI/LLM coding-assist on niche DSL, three-stacked-novelties. 10+ Deep-unique: reviewer COIs, license, index hints, slow-query forensics break, hiring pool, risk-allocation asymmetry, SLO-waiver, ranked alternatives, falsification thresholds, graduated rollout. 10 panel-wide misses surfaced only on 5th-reviewer (wire protocol/pool, runtime compile cost, migration tooling, APM coupling, CVE cadence, test ecosystem, recursive-CTE-as-DoS, generated-SQL stability across versions, proposer track record, spike pessimism-bias) — same architects-not-operators pattern as prior series. Stop iterating; remaining question is organisational.

---

# NeoQL adoption — final verdict (2026-05-13)

**Decision: DEFER / do not adopt as proposed.** 0 strict CHALLENGEs bidirectional; ~85% Deep/Fresh overlap; verdict stable across Deep×2 + Fresh×2.

**Why:** Pre-1.0 pre-production language (0 prod deploys, bus factor 1.5, v0.7 semver-permits-breakage) paired with the least forgiving constraints (customer-facing sub-second p95, recursive CTEs, window aggs, 5-way joins, 6-month deadline) on the *exact* workload its single-pass optimizer + undocumented advanced features cannot handle. Proposal is solution-first / problem-undefined (no incident, no benchmark, no acceptance criteria). Proposer has 4-vector COI (backend-lead + creator-correspondent + contractor budget authority); reviewer has 4-vector COI (prior collab + in-room weak endorsement + PM-as-spouse's-friend + 4-eng team).

**How to apply:** Default position on NeoQL-class proposals = defer. Five preconditions for re-evaluation: (a) written problem statement + acceptance criteria; (b) typed-SQL (sqlc/PgTyped/Kysely/jOOQ) + materialized-view baseline benchmarked against (a); (c) proposer + 3 COI-tied teammates recuse from vote; (d) falsification criteria + abandonment trigger committed pre-decision; (e) license/governance disclosure (CLA, trademark, relicense risk). Re-evaluate only after NeoQL v1.0 + ≥3 unrelated production deployments with reference-checkable customer-facing analytical workloads.

## Load-bearing chain
F2-2 (requirements = NeoQL's weak points, item-by-item) + C1 (no problem statement) + F2-11/M6 (reversibility asymmetric, generated SQL is non-source) + C6 (reversal cost personal/PR) + C5/F2-5 (12-engineer MTTR externality) + H5 (proposer COI undisclosed) + F1 (license/governance unknown). Any one suffices to defer; together adoption is indefensible.

## Issue counts
- CRITICAL: 8 (incl. mature alternatives as critical counterfactual)
- HIGH: 15
- MEDIUM: 6
- Process/structural: 3

## Calibration observations
- 0 strict CHALLENGEs bidirectional — every cross-reviewed point was AGREE or SYNTHESIZE-up; severity never moved down.
- Fresh-side systematic gap = severity-floor under-grading on consequence-chain items (MTTR externality, compile-to-SQL debug, reversibility, dialect leak).
- Deep-side systematic gap = governance/process items invisible from brief alone (no problem statement, reference-deployment-as-personal-commitment, proposer COI, reviewer COI, off-ramp non-source).
- Stop iterating. Remaining question is organisational (will recusal + falsification criteria be enforced?), not technical.

## Counter-proposal stable across all 4 sessions
Typed-SQL builder default (sqlc / PgTyped / Kysely / jOOQ) → materialized/incremental views for p95 lever → OLAP engine (ClickHouse / DuckDB / Druid) for analytical class → semantic layer (Cube / Malloy / LookML) acceptable only as thin layer over readable SQL → wait for NeoQL v1.0 + 3 unrelated prod deployments. Note: pilot-on-internal-tool is **structurally unavailable** (no adjacent low-stakes surface) — wait, don't pilot.
