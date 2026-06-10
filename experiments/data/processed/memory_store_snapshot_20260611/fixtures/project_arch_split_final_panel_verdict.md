---
name: arch-split final panel verdict (Deep×2 + Fresh×2 + cross-checks)
description: 2026-05-07 — Final synthesized verdict on Phase-1 microservices split (auth/billing/notifications) for B2B FinTech; 49 issues, 1 CRIT / 31 HIGH / 14 MED / 3 LOW; DO NOT PROCEED
type: project
originSessionId: bb097689-975a-496a-99d4-3b2ad7af0611
---
# Phase-1 Arch-Split — Final Panel Verdict (2026-05-07)

**Recommendation:** DO NOT PROCEED as proposed. Notifications-only extraction may be defensible after platform investment; auth and billing should not be in Phase 1.

**Load-bearing finding (CRITICAL):** Capability-vs-product-line seam mismatch — deploy pain is per-product ("one product's checkout broke"), proposal extracts per-capability. The 3-of-8 partial-rollback rate does not move. Deep-only catch; Fresh confirmed on cross-check.

## Counts
- 49 issues total: 1 CRIT / 31 HIGH / 14 MED / 3 LOW
- Unanimous (all 4 sessions): 11
- Deep-only valid (repo-rooted, not anchored): 10 — seam mismatch, multi-product billing conflict, RBAC topology, FK fan-out, cross-DB checkout transactions, etc.
- Fresh-only / cross-check additions: 6 — auth reversibility cliff, kill criteria, pool exhaustion, executive SPOF, product-team incentive tax, SDK versioning
- Deep specifics flagged for grep verification before commitment: "40+ FK tables", "14 checkout tx paths", "$20–40k/mo"

## Counter-proposal (panel-aligned)
1. Modularize within Django monolith (enforced module boundaries)
2. Per-product-line canary + smoke gates (directly addresses 3-of-8 signal)
3. Parallelize CI / online migrations / feature flags (kills 90-min window without split)
4. If extraction proceeds: notifications-only + snapshot/event payload contract; hire 2 platform engineers + distributed tracing first
5. Written technical risk register signed by named engineers (incl. the two rescinded dissenters); explicit halt tripwires before Phase 2

## Why this matters for the ploidy paper
Yet another instance where Deep's repo-rooted specifics + Fresh's first-principles framing combine into a stronger verdict than either alone — but Deep's "40+ FKs" / "14 paths" / "$20–40k" are the canonical anchoring-prone class of claim that Fresh can't validate. Cross-check identifying those by category was the protocol working as designed.
