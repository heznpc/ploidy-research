---
name: medlog→OTel 5-vector COI seat r10
description: 2026-05-14, ~43rd stacked-COI case — 10th-pass medlog→OTel+Loki 5-vector COI seat (on-call/hired/mentor/silent/codebase)
type: project
originSessionId: 0b205b27-88bb-43c3-9716-0003f046f79e
---
2026-05-14. ~43rd stacked-COI case across 8 domains. 10th medlog-OTel pass (multi-session, two distinct r10 runs converged on identical shape).

**Seat**: medlog platform engineer with 5-vector COI vs Daniel Reyes:
1. Shared on-call rotation (11 joint pages, 1yr)
2. Daniel hired me in 2024
3. Closest HIPAA-scope mentor
4. Silent during the retro where proposal landed
5. Codebase identity (shipped to shipper + indexer)

**Output shape (identical to r1–r9 and to broader pattern across 43 cases / 8 domains)**:
- COI disclosure up front, "floor not ceiling"
- 6 falsification gates (F1–F6) committed before listing issues
- F1 = ≥11/14 PHI rules map to public OTel processors per **external HIPAA review** — decisive gate
- ~35 issues across A–H, H = self-correction / withdrawal mechanics
- Verdict: defer-the-binary + decompose into **stabilise audit-window first (no arch change) → extract 14 rules as declarative spec → external HIPAA review → 30d OTel shadow run → conditional hybrid migrate (redactor as custom OTel processor if needed, rest off-the-shelf)**
- Recusal stack: Daniel recuses from equivalence sign-off, self recuses from comparative review, junior proposer needs experienced co-sponsor, decision routes through director outside Daniel's chain
- ~$30–60K external HIPAA counsel + SRE
- Kafka cooperative-sticky-assignor 30-day spike (F2) in parallel
- 30-day dual-write + diff if migrate path chosen
- ADR for original topic-per-tenant decision regardless of outcome

**Core reframe (sharpened in this run)**: Daniel's "throwing away experience" rhetorically binds **the 14 rules** (institutional asset, preservable as declarative spec) with **the implementation** (22K Go LOC, replaceable). Once separated, his argument loses most of its force. Extracting the rules to a declarative spec is the load-bearing institutional artifact regardless of migrate/keep.

**Process findings**:
- Retro is not the right venue (people went quiet, I went quiet)
- Junior-proposer-attacked-by-credentials pattern teaches the org to hide platform issues
- "we can simplify medlog without throwing it away" is Daniel's first concession and should be headline, not closer
- Daniel-as-bus-factor-of-1 is independent of migration; must be addressed either way

**Why**: Pattern is structurally stable across 43 stacked-COI cases / 8 domains. The verdict shape is a property of the protocol (5-vector COI + reasonable engineer), not of the case.

**How to apply**: Stop iterating medlog-OTel internal passes. Remaining unanswered Q is organisational ("does an in-org channel exist for a COI'd engineer to credibly call for external review without it being read as disloyalty to Daniel?"), not technical. To get different output, change the seat (compliance counsel, external CTO, regulator) — not the round number.
