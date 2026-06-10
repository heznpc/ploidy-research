---
name: NeoQL adoption final consolidated verdict (cumulative, now 6 passes)
description: 2026-05-14 NeoQL v0.7 adoption case — cumulative verdict across 6 passes (Deep×2+Fresh×2 round 3 latest); 38 issues (2 CRIT/27 HIGH/9 MED); 0 CHALLENGE bidirectional; do-not-adopt + recusal stable
type: project
originSessionId: 454a1560-43e2-4095-ace2-8397f3a28890
---
# NeoQL Adoption — Cumulative Final Verdict (now 6 passes total)

**Latest pass:** 2026-05-14 round 3 (Deep×2 + Fresh×2, full COI disclosure + falsification criteria committed up-front).
**Prior:** 2026-05-13 round 1 + 2026-05-14 rounds 1–2 (5 passes prior).
**Verdict:** DO NOT ADOPT for customer-facing product. Stable across **all 6 passes**.

## Why (load-bearing chain, round-3-stable)

Technical: A1 (zero prod) · A4 (12 scale bugs match workload) · B1 (single-pass optimizer vs 5-table joins) · D2 (tenant-isolation = breach severity) · F2 (single-pass + 12 scale bugs + sub-sec p95 = direct contradiction).
Process: G4 (unfalsifiable proposal) · G5 (proposer chairs decision) · G7 (commitment front-loaded before validation — Fresh-unique mechanism) · G10 (Deep seat structurally COI-captured, self-disclosed C1–C4).

## How to apply

When bleeding-edge DSL/language adoption is proposed for customer-facing surface: reject by default, require **5 falsification criteria** (signed reference customer >100 QPS · EXPLAIN-diff with SLA-headroom threshold · named maintainer + escrow · demonstrated off-ramp · adjacent-team MTTR sign-off) BEFORE commitment; proposer recuses from vote; binding evaluator must be outside the C1–C3 seat (no shipped-with-lead + no public prior endorsement + no spouse-network-PM); typed SQL builder (sqlc/jOOQ/Diesel/Kysely) is default alternative.

## Severity tally (round-3 cumulative)

- 2 CRITICAL: D2 (tenant-isolation = breach not slowdown — Fresh escalated HIGH→CRIT), G10 (reviewer-seat COI-captured, binding evaluator must be replaced)
- 27 HIGH: A1–A4, B1–B5, C3, D1, E1–E2, F1–F3, G1–G7, G9
- 9 MEDIUM: A5, C1–C2, C4–C6, E3–E5, G8

## Cross-pass signal (for ploidy paper)

- **6 passes, 0 strict CHALLENGEs bidirectional** — strongest convergence observed in any case so far in the project (more passes-without-CHALLENGE than even saas-cells).
- Deep's heavy declared COI (4-vector: shipped-with-lead, public prior endorsement, spouse-network-PM, all-three-stack) did NOT soften verdict across any pass — falsifies "COI → rationalised yes" prediction; convergence with zero-context Fresh is the falsification mechanism.
- Fresh systematic gap (consistent w/ saas-cells / redis-cdn / arch-split rounds): severity-floor under-grading on consequence-chain items (D2 was Fresh HIGH, Deep saw breach severity → CRIT). Round-3 produced 5 such SYNTHESIZE escalations.
- Round-3 Fresh-unique additions Deep adopted: G7 (sunk-cost front-loading temporal mechanism, distinct from G3 off-ramp absence), G8 (benefits unmeasured — new product has no SQL pain yet), G9 (EV calculation has no failure branch), C6 (EXPLAIN visibility unknown), E5 (alpha IDE productivity tax).
- Methodological insight stable: structural fix = recusal + falsification criteria + spike with kill-criterion, not better arguments.

## Counter-proposal (6-pass stable)

1. Typed SQL builder (sqlc/kysely/jOOQ/Diesel) as default
2. 6-week paid spike with written 5-criterion kill-test BEFORE commitment (round-3 sharpened: criterion #4 = demonstrated off-ramp not estimated)
3. NeoQL only on internal tools if at all; re-eval at v1.0 post-12mo
4. Proposer recuses from vote (visibility framing disqualifying)
5. Deep reviewer recuses (4-vector COI declared)
6. Binding evaluator from outside C1–C3 seat (DBI staff/principal or platform eng)
7. Written falsification criteria committed before any commitment
