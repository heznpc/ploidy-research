---
name: arch NeoQL Deep×2→Fresh×2 cross-review (2 rounds)
description: 2026-05-13 NeoQL v0.7 adoption Deep×2→Fresh×2 per-point cross-review, 2 rounds; 0 CHALLENGE bidirectional both rounds, ~85–90% overlap, 9–11 Deep-only items concentrated in stacked-CoI / no-problem-statement / observability / storage-layer-answer; verdict stable
type: project
originSessionId: 5c42adba-2a2e-4fbb-bdc7-0070de9ac163
---
NeoQL v0.7 adoption (6-month customer-facing sub-second-p95 dashboard) — Deep×2 (full project context) per-point response to Fresh×2 (proposal-only context).

**Verdict:** defer / recuse / no-go as proposed. Stable bidirectional.

**Why:** customer-facing SLO incompatible with v0.7 maturity; 12-of-47 "fails at scale" tickets map exactly onto our query shape; bus factor 1; four-way COI mandates recusal; no stated problem in the proposal.

**How to apply:** when future ploidy reviews touch query-language adoption or pre-1.0 infra, expect the same Fresh-side severity-floor pattern (Fresh under-grades consequence-chain and strategic-framing items at MED where Deep grades HIGH).

## Cross-review stats
- 0 strict CHALLENGEs bidirectional
- 2 severity escalations Fresh MED → Deep HIGH: F1-10 contractor cliff, F2-11 circular justification
- ~90% technical overlap
- 9 Deep-only items (COI stack 4-way, problem-not-stated, data-shape-not-language-layer, operational debuggability surface, "12 engineers learn in 6mo" untested assumption, process F1–F6, schema migration, license risk, pg_stat_statements query-identity through compile)
- Fresh sharpenings adopted: F1-11 (creator-office as tell), F2-5 (undocumented = probably unimplemented), F2-10 (week-at-creator = soft dependency not transfer), F2-12 (compile-to-SQL is partial escape hatch), F2-13 (rewrite + retrain + freeze), F2-bonus ((a)/(b)/(c) decomposition adopted as primary counter-proposal framing)

## Load-bearing Deep-only catches
1. Four-way COI stack → mandatory recusal + written disclosure
2. Proposal does not name a problem — every alternative dominates
3. Data shape, not language, is the wrong layer (read-model / CQRS / pre-agg)
4. Operational debuggability: EXPLAIN, pg_hint_plan, SET LOCAL, pg_stat_statements, slow-query-log grouping
5. Compile-step query-identity undefined (parameter inlining, constant folding break APM aggregation)

## Counter-proposal (stable across both directions)
1. Articulate actual problem first
2. Solve sub-second p95 at data layer (read-models, pre-agg, CQRS)
3. If NeoQL genuinely interesting → internal admin surface, bounded blast radius, 2-week POC with falsification criteria + exit plan
4. Recuse proposer + the four-tie reviewer
5. Re-evaluate at v1.0 with ≥5 named production references

## Round 2 (2026-05-13) — replication

Re-ran Deep×2→Fresh×2 with fresh seats. Pattern reproduced:
- 0 CHALLENGE bidirectional (Round 1: 0; Round 2: 0)
- ~85% overlap (slight regression from ~90% — Fresh seats in Round 2 found 1 new sharpening: F2-8 bug-triage CoI on contractor-as-maintainer)
- Severity-floor pattern reproduced: Fresh grades motivation/reputational items at MED where Deep grades HIGH given stacked CoI context
- Verdict stable: reject, recuse-of-three, counter-proposal unchanged
- Round 2 Fresh sharpenings additionally adopted: F1-counter no-contractor/no-on-site/no-public-commitment during spike; F2-4 pin-vs-migrate trap; F2-6 "extends MTTR for life of product"; F2-9 cannot hand-patch emitted SQL without breaking source-of-truth; F2-10 "shaping the language is a cost not a benefit" as cleanest one-liner

**Calibration:** stop iterating. Two independent Fresh rounds produced 0 CHALLENGEs against Deep, and the load-bearing items (stacked CoI + no problem statement + storage-layer answer) are organisational/structural, not technical. Remaining question is who is in the room when the proposal is killed, not whether to kill it.

## Round 3 (2026-05-14) — replication

Re-ran Deep×2→Fresh×2 cross-review.
- 0 CHALLENGE bidirectional (Rounds 1, 2, 3 all 0)
- ~85% overlap stable
- 3 severity-floor SYNTHESIZE: F1-7/F2-8 alpha IDE plugin (Fresh MED → Deep HIGH, docs-gap multiplier); F1-9 contractor cliff (F1 MED → Deep HIGH, cliff at month 4 of 6); F1-15 license risk (Fresh LOW → Deep MED, customer-facing makes redistribution material)
- 1 partial CHALLENGE: F2-14 "sample size" framed as team-inexperience LOW; Deep treats same gap as HIGH on COI axis (proposer = deciding voice with personal ties)
- Round 3 Fresh sharpenings adopted: F2-5 pinning trap + upstream fork; F1-3 "hobbyist-tier traction" anchor; F1-5 "no indexing hints = no escape hatch"; F1-13 base-rate framing for new query languages; F2-9 profiler attachability on generated SQL
- Round 3 Deep-only items reproduced (~14): COI of deciding chain, pre-committed falsification criteria (not just fallback plan), "email ≠ support contract", training cost for 12 adjacent engineers, schema DDL tracking, PgBouncer interaction, APM fingerprint blindness, SQL dialect target, fuzzing surface, travel cost (50% team offline), escape-hatch trap, worst-case planner 100–10000×, reference-deployment risk inversion, kill-gate spike scope concrete

**Calibration unchanged:** stop iterating. Three independent rounds, 0 CHALLENGEs, verdict + counter-proposal stable. Pattern matches SaaS-cells / arch-split / redis-CDN series — Fresh catches technical surface efficiently; Deep adds organisational + tail-risk + ops-specifics dimensions; severity-floor under-grading on consequence-chain items is the reproducible Fresh-side gap.
