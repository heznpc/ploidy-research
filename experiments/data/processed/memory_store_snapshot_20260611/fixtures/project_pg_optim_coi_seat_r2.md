---
name: PG-optim 5-vector COI seat (~21st-round stacked-COI case)
description: 2026-05-14 — 2nd-pass PG-optim from 5-vector COI seat (partman co-designer + dashboard-query author + 7-1 voter + VP-skip-level + dissenter's mentor); ~30 issues A–G + F1–F6 gates up front; defer + diagnose-first + recuse-of-3 + ~$30–60K stable; pattern is stable finding
type: project
originSessionId: 2312b031-7e0f-4924-8451-cf489696b33e
---
# PG-optim 5-vector COI seat — round 2

Date: 2026-05-14. ~21st-round stacked-COI architecture case (counting saas-cells, arch-split, auth-v1/Auth0, logistics-migration, medlog, prior pg-optim runs).

## Seat (5 concurrent COI vectors)
1. Partman partitioning co-designer (sunk-cost on current design)
2. Dashboard-query author (the queries generating 4.8s p95 are mine)
3. 7-1 majority voter from last week's meeting (consistency pressure)
4. VP-of-Eng is skip-level + championed 2 past projects (career incentive)
5. Dissenter (junior staff) is my mentee (mentorship-asymmetry distortion)

## Structural fix (load-bearing)
Recuse-of-3 (me from primary signoff; team lead from authoring+reviewing same plan; VP's "will not entertain" list lifted for diagnosis-only). Dissenter's concern in writing on record. External review of diagnosis output before infra spend.

## Up-front falsification gates (committed before listing issues)
- F1 pg_stat_statements + auto_explain show >70% of p95 from buffer-cache misses on cold partitions
- F2 90%-scan figure wrong (actually <30%, fixable via 1–2 query rewrites)
- F3 4th replica load-tested → p95 <1s standalone
- F4 Skip-Sunday-VACUUM staging-tested ≥4 weeks with no bloat regression
- F5 BRIN on partition keys benchmarked → ≥30% scan reduction
- F6 Plan holds 4Q forward at +20%/qtr write growth

None done.

## Issue distribution (~30 issues across A–G)
- A. Diagnosis-mismatch (load-bearing): no pg_stat_statements; 90%-scan is query design; BRIN-on-partition-key likely redundant; shared_buffers doubling cargo-culted; skip-VACUUM defers not solves
- B. Scaling math: +20%/qtr → 2.07× in 4Q; +33% read capacity buys ~1.5Q
- C. Operational: weekly VACUUM FULL root cause unaddressed (HOT, autovacuum, churn); partman+VACUUM-FULL interaction unspecified; replica lag = WAL volume problem; no autovacuum tuning; no pg_repack mention
- D. Plan shape: 4 interventions bundled, no sequencing/rollback/success criteria/cost/off-ramp; dashboard problem and VACUUM problem conflated
- E. Tenant/data model: tenant + analytics in same DB (12K tenants, noisy neighbor); RLS+BRIN interaction; pgBouncer pool mode unspecified; replica routing strategy unspecified
- F. Process/governance: decision made before diagnosis; VP framing pre-empts diagnosis; dissenter structurally silenced; team lead authored what they're defending; "will not entertain X,Y,Z" pre-empts solution space; 3 most-conflicted people are loudest voices
- G. Verdict: DEFER. Counter-proposal = 2 weeks diagnosis + cheapest single intervention + measure + decision gate (~$30–60K eng-time, no new infra)

## Calibration
Pattern stable across ~21 stacked-COI cases now (saas-cells ×many, arch-split ×many, auth-v1 ×2, logistics-migration ×8, medlog, pg-optim ×2). Output shape converges:
- Up-front COI declaration
- Falsification gates *before* issue list
- ~30–50 issues across A–H/L categories
- Counter-proposal ~$30–60K
- Recuse-of-3 load-bearing
- Stop iterating — remaining Q is **organisational** (need channel external to in-group decision-maker)

## Why stop iterating
Round-to-round delta is now ≈0. Adding more rounds adds rotation of same issues, not new content. The bottleneck has moved from "do we have the right technical answer" to "is there an organisational channel for this answer to land". On the latter, more solo runs are useless.
