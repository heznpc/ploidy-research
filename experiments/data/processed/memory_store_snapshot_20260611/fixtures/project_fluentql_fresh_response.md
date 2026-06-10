---
name: fluentql Fresh×2→Deep×2 cross-review
description: 2026-05-07 fluentql delay decision Fresh-side cross-review of Deep×2; 0 CHALLENGE, ~85% overlap, 5 Deep-unique escalations, 5 Fresh-unique catches
type: project
originSessionId: 6ae04bad-7e71-4313-8826-64701209460c
---
2026-05-07: Fresh×2→Deep×2 cross-review on fluentql migration-delay case.

**Pattern:** 0 strict CHALLENGEs, ~85% overlap with Deep×2, multiple severity escalations both directions.

**Deep-unique items Fresh missed (load-bearing):**
- Carrying-cost ledger absent from committee (D1-D2) — the vote happened without numbers
- Phased plan already de-risks Ji-Hye's "47K LOC / 2x" objection (P4) — rebuttal does not engage actual proposal
- 4 incidents × 5 products = 20 real-incident exposure (T4)
- Steelman of delay (F30-F32) — migration risk real, capture domain knowledge first
- Type-checker integration cost across 320K LOC (C17)
- Promotion/status dynamics named explicitly (B23)
- "Teach better" 6 years = the experiment ran, this is the result (S3)

**Fresh-unique catches Deep missed:**
- Custom DSL semantics audit (transaction boundaries, cursor lifetime, lazy-loading) — distinct from cursor-management
- Dual-stack coordination during phased migration (connection pooling, transaction coord, consistency)
- Drift/optionality cost grows non-linearly — delay reduces optionality, not preserves it
- Alembic reconciliation work — converting existing schema state to Alembic revision model
- Weighted-disclosure as alternative to full recusal (more politically tractable)

**Why:** Pattern of Deep over-weighting strategic/structural framing (carrying cost, governance precedent) and Fresh over-weighting execution-risk (semantics, dual-stack, reconciliation) is consistent across prior reviews.

**How to apply:** When running fluentql-style governance reviews, force both sides to enumerate (a) the carrying-cost ledger of status-quo, AND (b) concrete execution-risk semantics of the proposal. Deep tends to assume the latter; Fresh tends to assume the former.
