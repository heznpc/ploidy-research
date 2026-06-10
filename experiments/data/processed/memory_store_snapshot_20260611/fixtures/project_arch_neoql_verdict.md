---
name: NeoQL v0.7 adoption verdict
description: 2026-05-14 Deep×2+Fresh×2 NeoQL adoption for 6mo customer-facing dashboard — 40 issues (4 CRIT/22 HIGH/12 MED/2 LOW); 0 strict CHALLENGE bidirectional, 1 meta-CHALLENGE (Deep's "second seat with COI controlled" = anchoring leak); defer + Postgres+typed-builder counter-proposal + proposer+reviewer recusal stable
type: project
originSessionId: e0ea023f-86ac-46ff-a7af-0cf4e462a35e
---
# NeoQL v0.7 adoption — final verdict (2026-05-14)

**Proposal:** Adopt NeoQL v0.7 as query layer for 6-month sub-second customer-facing dashboard product. Backend lead is proposer; 4-engineer team; 12 adjacent engineers; contractor 3mo + creator-office visit 1wk.

**Verdict:** DEFER. Adopt counter-proposal (Postgres + typed builder + read-model store). Time-box NeoQL spike on non-customer-facing internal tool with explicit kill criteria. Proposer + conflicted reviewer (Deep S1) recused; external platform/DBA reviewer adjudicates.

## Convergence stats
- Total: 40 confirmed (4 CRIT / 22 HIGH / 12 MED / 2 LOW)
- 0 strict technical CHALLENGEs bidirectional across 4 sessions
- 1 meta-CHALLENGE: Fresh flagged Deep S1's offer to "run another Ploidy debate as second seat with COI controlled" as anchoring leak (recuse cleanly OR vote on merits, not both)
- 3 severity-floor SYNTHESIZEs (Fresh under-grades second-order consequence chains — same pattern as SaaS-cells, Redis-CDN)
- ~85% overlap on technical risk

## Load-bearing structural findings
- **C1: Proposal does not state the problem it solves.** Most load-bearing single finding (Deep S2 elevated from Fresh S2 hint). Without a named pain, every NeoQL risk is taken in exchange for unspecified benefit.
- **C2: Reviewer COI (Deep S1).** 2-yr history with proposer (recruited reviewer), public "sounds exciting" pre-commitment, PM is spouse's college friend. Structurally invisible to Fresh.
- **C3: Proposer not recused from career-beneficial decision.**
- **C4: No exit/falsification criteria + no rollback plan.** Fresh S1 sharpens — month-4-of-6 switching cliff makes sunk-cost lock-in irreversible.

## Fresh-unique catches Deep missed (7)
1. **H8 underlying database unspecified** — sub-second p95 depends heavily on target engine (Postgres/column-store/OLAP), NeoQL dialect coverage on that engine unstated
2. **H19 bidirectional creator-relationship sunk cost** — office visit creates future-bias mechanism for "should we switch off?", not just present-tense motive
3. Production-only failure mode enumeration (pooling, long-running queries, memory under load, error recovery)
4. "Team owns a fork of a Rust compiler" as concrete cost framing
5. Upstream-bug-roundtrip cycle time as schedule mechanism
6. "Reference deployment" framing makes retreat expensive even when correct
7. Generated SQL from single-pass optimizer will be *bad*, not just present

## Deep-unique catches Fresh missed (10)
- License/relicense risk (BSL/SSPL conversion typical at v0.7 + VC arrival)
- No documented raw-SQL escape hatch
- Bus-factor-of-2 by construction (plan literally says "send 2 engineers")
- NeoQL hiring market = 3 employed people on Earth
- No decomposed cost (contractor $, offsite $, 2× eng-weeks, ongoing read-tax)
- Decision venue mismatch (4-eng room, no platform-eng/DBA)
- Reference-deployment = lifetime upstream-support load
- Migration off custom DSL is asymmetrically harder than off SQL
- Hiring narrative is currently liability not asset
- COI / recusal / "sounds exciting" pre-commitment cluster (structurally invisible to Fresh)

## Counter-proposal (stable across all 4 sessions)
1. Postgres + typed builder (sqlc/Kysely/jOOQ)
2. Materialized views or read-model store (ClickHouse/DuckDB) for sub-second p95
3. Optional NeoQL spike on non-customer-facing internal tool, 2–4 wk, kill criteria pre-committed
4. Written decision artifact reviewed by external platform engineer
5. Proposer recused; Deep S1 recused cleanly; external reviewer adjudicates

## Calibration
Stop iterating. Pattern matches SaaS-cells and Redis-CDN (0 CHALLENGE bidirectional, ~85% overlap, Fresh severity-floor on consequence chains, Deep-only on COI/process). Remaining question is organisational (will proposer + Deep S1 recuse, will external reviewer be retained), not technical.
