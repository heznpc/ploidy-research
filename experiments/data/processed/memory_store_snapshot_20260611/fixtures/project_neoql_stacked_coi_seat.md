---
name: NeoQL adoption single-seat eval (4-vector COI incl. public stance)
description: 2026-05-14 single-seat NeoQL v0.7 adoption eval, 4-vector COI (prior-collab w/ lead, public 'sounds exciting' stance, PM-spouse-friend, lead-hired-me); reject + recuse stable
type: project
originSessionId: fa1a2f40-d6b0-4050-a7ce-7d7322b1a43b
---
2026-05-14: Single-seat eval of NeoQL v0.7 adoption proposal. Customer-facing analytics dashboard, 4 eng + 1 PM, 6mo launch, sub-second p95, 5-table joins + recursive CTE + window agg.

**Why this is a new entry alongside project_neoql_deep_response_v2.md:** The earlier file is a panel Deep×2→Fresh×2 round on the same case. This file captures the stacked-COI single-seat variant — parallel to the SaaS-cells emp#4 / auth-v1 stacked-COI / fluentql-deprecation-colleague-seat / push-forward proxy-author pattern.

**Novel COI vector in this case:** prior *public stance* in the room ("sounds exciting") creates consistency-pressure distinct from relational/social vectors in prior cases. Should be explicitly named in COI disclosure for any future case where the seat has prior public position-taking.

**How to apply:** When future single-seat evals are requested with stacked COI, replicate: (1) COI disclosure up front, (2) falsification gates committed before issue list, (3) issues with confidence levels, (4) verdict + counter-proposal + recusal recommendation, (5) calibration note that this seat is the wrong decision-maker.

**Verdict:** Reject, HIGH confidence. Convergent with project_neoql_deep_response_v2.md. Three load-bearing axes:
- Capability: single-pass optimizer + undocumented window/recursion + 12 known scale bugs vs sub-second p95 on 5-table joins + window aggregations
- Maturity: 0 production deployments + bus-factor-1 maintainer + pre-1.0 API + no reference customers at scale
- Governance: promotion-optics framing ("we'll be the company that proved it"), undeclared lead-creator COI (QCon contact), no falsification gate, customer-facing critical path selected as first deployment

**Falsification gates committed up front:** F1 spike-demonstrated p95, F2 ≥5 maintainers/≥2 FT, F3 reference customer at scale, F4 12 scale-bugs closed, F5 documented window+CTE+index-hint, F6 license clean of upstream IP claim. None met.

**Counter-proposal:** Plain SQL + thin composition lib (or dbt + PG views) for product; 2-week internal-only NeoQL spike gated on F1–F6; recuse proposer + 4-vector-COI seat + PM-as-spouse-friend; capture "shape the language" upside via 1-engineer 20%-time OSS contribution with no production dependency.

**Calibration:** This seat (4-vector COI including public consistency pressure) is the wrong decision-maker. Next step is recusing and having an unconflicted reviewer reproduce/refute F1–F6.
