---
name: NeoQL v0.7 adoption — 5-vector COI seat r3
description: 2026-05-14 3rd-pass NeoQL adoption eval from 5-vector COI seat; ~30 issues A–H + F1–F6; defer + Postgres-typed-builder + recuse-lead-and-self stable across 3 runs; ~16th stacked-COI case
type: project
originSessionId: bd7f64a6-c00a-45f9-b16c-44879c89639e
---
2026-05-14. 3rd-pass NeoQL v0.7 adoption eval (4-eng dashboard team, 280-emp analytics co). Replicates r1 + r2 findings.

**COI vectors (5):** tenure-paired w/ lead, in-room "sounds exciting" non-dissent, PM = spouse's college friend, team-seat dependency, identity-coded early-adopter framing.

**F1–F6 falsification gates committed up front:** ≥1 prod deployment at scale; reference docs for window/recursive/index-hints; v1.0 LTS policy; ≥2 full-time non-same-entity maintainers + 12mo commitment; compiled-SQL within 20% of hand-tuned on our 3 hardest queries; ≥10 NeoQL-on-resume candidates. Expect ≤1 to clear in 30 days.

**~30 issues across A–H:** A tech readiness (v0.7 pre-1.0, 0 prod, 12/47 fails-at-scale, single-pass optimizer, missing docs for required features) / B bus-factor & vendor (3 maintainers, "have his email"=liability, no LTS, contractor exit) / C hiring/on-call (12 adjacent eng can't read it, ~0 hiring market, knowledge concentration in 2 trip attendees) / D schedule (6mo+v0.7 reckless, no off-ramp, too many novel variables) / E perf+correctness on our workload (sub-sec p95 unproven, recursive-CTE correctness landmine, window-agg w/o index hints, no EXPLAIN) / F decision process (resume-driven framing, one-sided cost/benefit, proposer-as-sole-evaluator, social-proof argument, in-room consent ≠ endorsement, two consent-via-relationship problems on 4-eng team) / G $ (~$80–150K year-1 OOM, typed-query-builder alt at <5% risk) / H governance (no external review, no pre-committed off-ramp, in-group cannot self-review).

**Verdict (stable 3 runs):** Do not adopt. Ship on Postgres + typed query builder (sqlc/Kysely/jOOQ/Drizzle). Re-evaluate at v1.0 with F1–F6 gates. 2-week spike outside critical path acceptable. Recuse lead + self.

**Pattern (~16th stacked-COI case):** output shape stable; remaining question always organisational not technical — route to channel external to in-group.
