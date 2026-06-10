---
name: fluentql_final_v5
description: 2026-05-07 Round-5 final fluentql deprecation verdict — 56 issues (4 CRIT/31 HIGH/17 MED); 0 CHALLENGE bidirectional 5 rounds; load-bearing G1+G2+G3+O5+P8+R2; recommendation (vacate, recuse, harden, Alembic-first) stable
type: project
originSessionId: 4d59c847-4ddc-4488-8bf5-e1d7f8cfa783
---
Round-5 Deep×2+Fresh×2+5th-Fresh consolidated verdict on fluentql deprecation.

**56 confirmed issues:** 4 CRITICAL / 31 HIGH / 17 MEDIUM / 0 LOW.
- CRITICAL: G1 (COI swing vote), G2 (recusal protocol never raised), G3 (with recusal it's 3-3), O5 (no carrying-cost ledger).
- 0 strict CHALLENGE bidirectional across 5 rounds.

**Load-bearing chain:** COI swing → no recusal protocol → outcome inverts → no carrying-cost ledger → "teach better" already falsified by 6yr × 11/14 → Alembic-first decouples and ships value.

**Fresh-unique catches:** psycopg2 EOL (T6), committee never reviewed postmortems (G8), SQLA hiring funnel (O3), false dichotomy / no third option (G12).

**Deep-only catches:** code-review authority asymmetry (G4), abstention-as-coerced-data (G5), chilling effect (G9), attrition-as-coercion (G10), compounding no-async cost (T2), custom DSL = SQLi surface (T5), Phase 0 POC with pre-registered metrics (R4), Alembic-first as decoupled shipping wedge (T4/R2), "47K lines" rhetorical framing (P6).

**5th-reviewer panel-wide gaps (M1–M8):** wrong-question/charter framing, anchored-number provenance, symmetric proposer-side COI, "process invalid → migrate" non sequitur, re-vote cost, today's 5-product migration risk, political-technical coupling, external-audit option.

**Severity-floor pattern:** Fresh consistently under-grades consequence-chain items at MED that Deep grades HIGH (escalations: G6, G7, G9, G12, P4, P7, T1, T3, R5, R8). Mechanism: Fresh sees items in isolation; Deep sees how items compose into the load-bearing chain.

**Recommendation (stable 5 rounds):**
1. Vacate the 4-3 vote.
2. Re-vote with Ji-Hye recused; abstainers required to recuse-or-vote (not abstain); private polling for cause.
3. Approve in principle, harden plan: Alembic-first decoupled, Phase 0 POC with kill-switch + pre-registered metrics (latency, LOC delta, incident rate, onboarding-time-to-PR), test-coverage audit of call sites, costed estimate from independent party, reverse off-ramp triggers, dual-stack coordination plan.
4. Do not "teach fluentql better" — that experiment ran for 6 years; 11/14 is the result.

**Calibration call:** Panel has converged. Further rounds unlikely to surface new load-bearing items.
