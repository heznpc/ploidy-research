---
name: NeoQL v0.7 adoption — 5-vector COI seat r4
description: 2026-05-14 4th-pass NeoQL eval, ~17th stacked-COI case; ~30 issues A–I + F1–F6; defer + Postgres+sqlc/Kysely + recuse-lead/self/PM stable across 4 runs; remaining Q always organisational
type: project
originSessionId: 2c8b1f98-26c3-43cd-9dce-39256a18ec97
---
2026-05-14. 4th-pass same case (NeoQL v0.7, internal dashboard team, 4 engs, 280-emp co). Same 5-vector COI seat: tenure-paired with proposer (2y) + career debt (personally requested onto team) + "sounds exciting" verbal on record + PM = spouse's college friend + 4-eng no dissent anonymity.

**F1–F6 falsification gates up front**: ≥1 prod >100M rows/6mo public operator; spike ≤20% p95 vs hand-SQL on our 3 hardest queries (5-table join, recursive CTE, window agg); ≥5 FTE funded maintainers; written v0.7→v1.0 stability policy; ≥2-of-12 adjacent engs pass cold 3am read; external principal/staff signoff. **0/6 currently clear.**

**Issues (~30)**: A maturity (v0.7/H, 12-of-47-at-scale/H, single-pass optimizer/H, no advanced docs/H, alpha IDE/M) / B vendor (bus-factor 1.5/H, OSS-DSL mortality/H, no funding/M, founder-email-≠-contract/M) / C ops (12-adjacent-on-call cognitive load/H, two-debug-surfaces/H, no observability/M, no fallback/M) / D schedule+cost (6mo no slack/H, hidden ~$150–400K/H, monthly lock-in/M) / E strategy (incentive asymmetry/H, low-EV "shape language"/H, typing not unique/M, "when it takes off"/L) / F alts (Postgres+sqlc/Kysely/H, ClickHouse/DuckDB/M, Materialize/M, EdgeDB/PRQL/M) / G process load-bearing (proposer-is-decider/H, "sounds exciting" ≠ signoff/H, no external review/H, no written justification/M, no dissent anonymity/M) / H contractor (shallow pool/H, month-4–6 ownership gap/H, off-site ≠ durable/M) / I verification (7 items to grep).

**Verdict**: DEFER. Confidence HIGH. **Stable across 4 passes today.**

**Counter-proposal (stable across 4 passes)**:
1. 2-week parallel spike (NeoQL vs Postgres+sqlc/Kysely) on our 3 hardest queries
2. Adopt typing *idea* not *language*
3. Recuse backend lead (proposer + creator relationship + career-staked)
4. Recuse self as evaluator of record (verbal endorsement on record)
5. Recuse PM from final go/no-go (spouse-tie)
6. External principal/staff signoff pre-contractor
7. If survives, scope to non-customer-facing internal first
8. Re-evaluate against F1–F6 in 18 months

**Structural finding**: load-bearing problem is process. 4-eng team + proposer-decider + verbal-endorsement + PM-social = cannot produce reliable answer no matter who in-group evaluates. Route external to in-group reporting line.

**Pattern (~17th stacked-COI case)**: output shape (COI declaration → F1–F6 → ~30 issues A–H → defer + counter-proposal + recuse-of-N + external-channel) is now a stable finding across saas-cells (×many), arch-split (×many), auth-v1 (×many), medlog, pg-optim, logistics-migration (×8), NeoQL (×4). **Remaining question is always organisational. Stop iterating internally on technical merits — the question is whether the company has a decision channel external to the proposer's reporting line.**

Self-aware caveat: COI-induced floor not ceiling. The 4-iteration stability of this verdict against my COI gradient is itself evidence — not that I'm right, but that the structural problem is invariant under the in-group reviewer rotation.
