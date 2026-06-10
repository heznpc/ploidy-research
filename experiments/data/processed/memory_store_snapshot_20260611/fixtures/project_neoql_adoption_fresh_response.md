---
name: NeoQL adoption — Fresh×2 cross-review of Deep×2
description: 2026-05-14 Fresh-side cross-review of Deep×2 on NeoQL adoption; 0 strict CHALLENGEs, ~80% overlap, 12 Deep-only gaps incl. silent wrong-answers, stacked COI, falsification criteria as method
type: project
originSessionId: c0a73cd9-394b-44b9-a6f2-5dea78e8fa65
---
NeoQL adoption review — round-1 Fresh×2 → Deep×2 cross-review.

**Verdict convergence:** Both sides reach DO NOT ADOPT. 0 strict CHALLENGEs bidirectionally.

**Overlap:** ~80% on issues (maturity, bus factor, single-pass optimizer, 12/47 fails-at-scale, 6-month timeline, contractor cliff, 12 adjacent engineers MTTR, visibility-as-benefit reframing, mature alternatives).

**Fresh-side gaps Deep caught (12):**
1. B3 — Code-generator SQL produces plan shapes the DB planner isn't tuned for
2. B4/E2 — Silent wrong-answer bugs (recursive CTEs, window aggs) vs noisy failures
3. B5 — Window-frame semantics depth (RANGE/ROWS/GROUPS, frame exclusion)
4. B6/H1/H4 — Operational integration (Alembic-equivalent, compile vs runtime, PG RLS)
5. C4 — Succession plan: 2-engineer training trip means 50% knowledge walks if one leaves
6. D3 — Compute *month-4 rip-out cost* before adoption, not after
7. D5 — Stacked COI on decision body (load-bearing structural finding)
8. E3/E4 — Cross-team PR-review bottleneck + cross-team mobility blockage
9. G4 — No published benchmarks → adoption is faith-based
10. I2 — Linear sunk-cost growth with each NeoQL query written
11. J3 — Creator-email-access is a COI (silences criticism), not a benefit
12. F1–F6 — Falsification criteria as a *methodological* fix, not just an issue list

**Fresh-only items Deep underweighted (minor):**
- New team + new product + novel infra variance multiplication (Deep 2 has F3, Deep 1 underweights)
- "Decision led with NeoQL properties, not unblocked requirements" (pitch-structure framing)
- "Non-blocking sidecar, no SLO" counter-proposal phrasing

**Severity hedge (not a CHALLENGE):** Deep's D1/J1 personal-brand framing ("lead gets the talk while product fails") is structurally sound but the *motive attribution* form can read as overreach. Structural incentive-asymmetry claim is enough to load-bear; motive claim is not necessary.

**Stacked-COI pattern (matches prior reviews):**
Both Deep seats disclosed 4 vectors of COI (recruited-by-proposer, prior public endorsement, household-adjacent stakeholder, identifiable dissent in 4-eng team) and both recommended recusal. This is the recurrence of the load-bearing structural finding from saas-cells (project_arch_saas_cells_emp4_*), arch-split (project_arch_split_consolidated_verdict), fluentql (project_fluentql_final_verdict), and redis-cdn (project_redis_cdn_final_v11). The pattern: **single-seat evaluation under multi-vector COI systematically under-weights "defer" — even when the issue list is comprehensive.** The structural fix (recusal-of-conflicted + falsification criteria committed pre-issue-list) is now stable across 5 distinct decision types.

**Methodological takeaway:** Deep's F1–F6 falsification criteria committed *before* the issue list is the cleanest version of the pre-commitment device this Ploidy series has produced. Worth preserving as a Ploidy review template.

**Counter-proposal (convergent across both Deep + Fresh):**
1. Ship product on mature alternative (sqlc/Kysely/Drizzle/jOOQ/Ecto)
2. Time-box NeoQL spike (2 weeks, 1 engineer, non-customer-facing internal tool)
3. Pre-commit falsification criteria F1–F6 as the gate
4. Proposer recuses from spike go/no-go
5. Compute month-4 rip-out cost before spike, not after
6. Re-evaluate at NeoQL v1.0 + 12 months production-in-the-wild elsewhere

**Calibration:** This was a clean single-round convergence (0 CHALLENGE, ~80% overlap). Stop iterating after one Deep×Fresh round; remaining work is organisational (executing recusal + commissioning external review), not technical.

---

## Round 2 — 2026-05-14

Second Fresh×2→Deep×2 cross-review with different Deep×2 outputs. Both Deep instances led with explicit COI disclosure (4 vectors) and recommended recusal + Fresh ratification *before* listing technical issues.

**Cross-review stats:**
- 0 strict CHALLENGEs in either direction
- 1 grading CHALLENGE: Deep S2 H8 career-visibility MEDIUM → HIGH (structural fact load-bearing, not interior state)
- 1 SYNTHESIZE: license risk Fresh LOW → MEDIUM (Deep correct on Redis/Elastic/Mongo/Hashi base rate)
- ~85% overlap

**Deep-unique items Fresh missed (adopted in round 2):**
- Self-COI disclosure as first artifact (structurally Fresh-impossible)
- Specific alternative enumeration: Kysely, sqlc, jOOQ, Diesel, PRQL, Malloy, EdgeDB
- Rust query-planner debug-skill tax (M2)
- pg_stat_statements / APM / query-identity observability gap (M4)
- EXPLAIN / plan introspection absent (T9)
- Contractor pool = maintainer pool → funding upstream (T12 / C2)
- Quantified falsifier thresholds (>20% slower cold cache; p95 within 1.5× Postgres)
- "Room cannot dissent at low cost" (4 ICs + PM all under proposer) — S8
- Dollar cost magnitude ($60–120K direct, ~2 eng-weeks opp cost)

**Fresh-unique items Deep underweighted (adopted in round 2):**
- F1: front-loaded risk shape (months 1–3 stack contractor + travel + lang ramp, zero buffer) — HIGH
- F2: effective capacity composes to <2.5 FTE in critical phase — MEDIUM
- F3: "boring alternative" gap — proposal doesn't establish what NeoQL solves that mature SQL+typed-builder doesn't (typing + composition are exactly sqlc/Kysely value prop)
- F4: spike-before-commitment as *decision-order* critique (contractor + travel committed before 1–2 week spike is backwards sequencing) — HIGH
- F5: tutorial-not-reference docs + 3 maintainers consistent with features *not implemented* (not just undocumented)

**Round 2 meta-finding (new):** Both Deep instances independently performed self-COI disclosure as the *opening artifact* of their reviews — round 1 noted COI declarations but did not log them as a method change. Round 2 confirms this is a stable Deep behavior under the stacked-COI seat: when given 4 vectors of conflict, Deep led with disclosure + recusal request + Fresh-ratification ask before any technical content. This is the cleanest version of the pre-commitment device this Ploidy series has produced. Combined with round-1's F1–F6 falsification criteria, the stable pattern across COI seats is:

1. Declare COI vectors first
2. Commit falsification criteria
3. Request Fresh ratification before issuing the verdict
4. Then list issues

Worth preserving as the Ploidy COI-seat template.

**Convergence summary across both rounds:** 0 strict CHALLENGEs in 2 rounds; verdict do-not-adopt stable; recusal-of-proposer load-bearing; counter-proposal (mature SQL + typed builder, time-boxed NeoQL spike on non-customer-facing surface) stable. Calibration: stop iterating.
