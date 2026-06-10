---
name: NeoQL adoption 5th-reviewer fresh cross-check
description: 2026-05-14 — Fresh 5th-reviewer cross-check on Fresh×2+Deep×2 NeoQL adoption review; 0 CHALLENGE bidirectional, 11 panel-wide gaps, defer verdict stable
type: project
originSessionId: 0fad6166-bb23-45c5-8393-74c096135f5a
---
2026-05-14: 5th-reviewer Fresh cross-check on the NeoQL (v0.7 query language) adoption debate.

**Topic:** 4-engineer team proposing v0.7 NeoQL for a 6-month customer-facing sub-second p95 dashboard product.

**Calibration:** 0 strict CHALLENGEs across both Fresh×2 and Deep×2 sides. High overlap on load-bearing items. Defer verdict stable across all 5 reviewer-passes.

**Load-bearing chain (priority order):**
1. No named technical problem (Deep #1) — without quantified pain, typed SQL builder dominates.
2. Wrong layer for the perf problem — sub-second p95 on 5-table joins + recursive CTEs is storage/precomputation, not query-language (Deep #1 alternatives #2).
3. Requirement ↔ documented-weakness collision (recursion, windows, indexing hints undocumented + scale-fragile).
4. Proposer COI + no architecture review (process structurally broken).
5. Externalised cost on 12 adjacent engineers during incidents (team-level decision binding org-level resources).

**Deep-unique items 5th-reviewer confirmed:**
- A5 license/governance (RSAL/BSL relicensing risk on single-vendor pre-1.0)
- C2 no indexing hint syntax (can't force plan during incident)
- C3 APM tags generated SQL not NeoQL (Datadog/pganalyze mismatch)
- C5 schema/migration tooling gap (Alembic/sqlc don't know NeoQL)
- D3 internal mobility blocked bidirectionally
- E2 commercial/IP terms for creator office-visit undefined
- F3 no architecture/SRE/security review on compiler in request path
- F4 proposer COI not declared in proposal
- F5 base rate <5% for v0.7 single-vendor DSLs reaching mainstream
- G1 security review of new compiler (injection surface, schema leakage, supply chain)
- G2 backups/DR non-determinism across compiler versions
- Problem-statement absence (Deep #1 root cause)
- Materialised view / read-model as actual answer (Deep #1)
- Sunk-cost check naming "pressure is social, not technical"

**5th-reviewer additions (panel-wide gaps):**
- SLO/SLI/error-budget undefined before language choice
- Compiler-in-request-path supply-chain attack surface
- Schema/migration coupling with compiler-cached schema metadata
- Observability query-hash stability across compiler versions
- Connection pooling / prepared-statement reuse mismatch with PgBouncer
- Compliance/audit trail across compiler version drift
- Asymmetric, uncapped cost of being wrong
- Falsification asymmetry ("right" hard to falsify, "wrong" only by prod failure)

**Severity floors recommended (both sides under-graded):**
- Two-layer debugging (Fresh MED → HIGH; Deep already HIGH)
- Customer-facing externalisation (Fresh MED → HIGH)
- Org-level decision at team level (F2-11 MED → HIGH)
- Typed-SQL-builder absence as comparison (MED → HIGH)
- No prototype/spike (HIGH → CRITICAL)

**Why:** Adoption-of-v0.7-compiler-in-customer-facing-request-path is a high-asymmetry decision under structural COI; cross-checking across 5 contexts produces a stable defer + recusal-of-proposer + spike-with-kill-criteria + typed-SQL-builder alternative.

**How to apply:** Reuse the 5-pass pattern (Fresh×2 + Deep×2 + Fresh-5th) for any "new infrastructure dependency in the request path" decision where proposer has career incentive. Stop iterating once 0-CHALLENGE bidirectional + verdict stable across passes — remaining questions are organisational, not technical.
