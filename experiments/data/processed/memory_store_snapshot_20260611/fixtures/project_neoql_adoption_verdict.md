---
name: NeoQL adoption Deep×2 × Fresh×2 verdict
description: 2026-05-14 NeoQL v0.7 adoption proposal — 4-session debate, DO NOT PROCEED, 38 confirmed issues, counter-proposal = typed SQL builder + sealed PoC
type: project
originSessionId: 9b4cea65-70ba-4346-ac6d-6d224e736dc4
---
2026-05-14: NeoQL v0.7 adoption proposal for customer-facing analytics product (6-month launch, sub-second p95, 5-table joins + recursive CTEs + window functions).

**Verdict across 4 sessions: unanimous DO NOT PROCEED.** 0 strict CHALLENGEs bidirectional. 3 SYNTHESIZE items.

**Why:** Deep reviewers had 4-COI stack (recruitment dependency, on-record endorsement, spouse-channel PM, single-source proposer) yet still rejected — Fresh seats independently reached same verdict with no team context. Convergence under COI-pressure-against-rejection is strong signal.

**How to apply:** When evaluating early-stage tooling adoption proposals for customer-facing critical-path systems, the load-bearing items are: (a) zero prod deployments anywhere, (b) requirements directly contradict documented features, (c) failure-mode-disclosed-in-issue-tracker matches workload regime, (d) no off-ramp + no falsification criteria, (e) proposer COI undeclared. Counter-proposal shape: typed SQL builder default + 1–2 week sealed PoC with pre-committed falsifier + recusal-structured binding vote *before* contractor hire.

**5th-reviewer adds** (panel-wide misses):
- pg_stat_statements / APM query identity preservation through SQL normalisation
- Schema migration tooling integration
- pgBouncer + prepared-statement cache parametrisation behaviour
- CI test infra cost for asserting compiled-SQL correctness
- Recusal mechanics — who calls vote, who sits on it
- Decision sequencing: license check → issue triage → sealed PoC → recusal vote → contractor

**3 SYNTHESIZE items:**
1. Single-pass optimizer framing — risk is *compiler shape-locks generated SQL*, not "no multi-pass optimisation exists" (Postgres planner still runs). Falsifier: compare generated SQL plan quality to hand-written on cold cache.
2. "Contractor-to-bootstrap is competence signal" → reframe as month-3 handoff cliff (mechanism > framing).
3. License risk: D1 HIGH vs F2 LOW → MEDIUM (real but traction-conditional).

**Counter-proposal stable across both rounds:** Kysely/sqlc/jOOQ default; sealed 1–2 week PoC with pre-committed p95 falsifier; NeoQL on internal-only surface if PoC passes; re-evaluate at v1.0 with ≥1 named non-pilot prod deployment; backend lead + 4-COI reviewer recuse from binding vote.

**Calibration call:** stop iterating. Remaining question is organisational (will team actually recuse proposer and run sealed spike?), not technical.
