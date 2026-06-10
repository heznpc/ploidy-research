---
name: FinTech monolith→microservices stacked-COI seat
description: 2026-05-28 stacked-COI eval of FinTech B2B monolith→microservices split from senior-engineer seat (4 COIs); ~25 issues A–F + 6 falsification gates; recommendation = recuse, external review, rescope Phase 1 to notifications-only
type: project
originSessionId: dc1a31c3-5868-4662-8fc7-2a53ce608c46
---
2026-05-28 stacked-COI architecture eval: FinTech B2B (200 emp, 280K LOC Django, 2.4M req/day) monolith → 5 services in 6mo per CTO directive; Phase 1 = auth + billing + notifications, 1 quarter each.

**Seat COIs (4 vectors):**
1. CTO promoted me to senior (promotion lineage bias)
2. I liked the all-hands Slack message (public agreement on record)
3. The 2 rescinded-concern engineers sit next to me (adjacency to silenced dissent)
4. I wrote ~1/3 of the checkout module that auth+billing touch (sunk authorship)

**Output shape (matches ~60+ prior stacked-COI cases — auth-v1, SaaS-cells):**
- COI disclosure before content
- Issue list A (diagnosis unproven), B (org/capacity gap), C (architectural correctness incl. distributed-txn on checkout + availability math 0.9995^4≈99.80%), D (PCI/SOC2/residency), E (infra cost), F (governance — "not a debate" + rescinded concerns + no falsification criteria)
- 6 falsification gates as withdrawal conditions for Phase 2
- Recommendation: recuse, external review, rescope Phase 1 to notifications-only

**Load-bearing technical findings:**
- C3: billing-with-own-DB → distributed-txn problem on checkout, none of {2PC, saga, eventual} specified → silent double-charge / lost-revenue risk
- C2: availability math 99.95%^4 ≈ 99.80% = ~4× downtime before counting new failure modes
- C6: sequencing inverted — notifications (low-risk) should be Phase 1 learning vehicle, not bundled with auth+billing (critical path)
- A2: "3 of 8 partial rollbacks in checkout" — microservices make atomic rollback HARDER, contradicts the stated motivation

**Why:** Memory tracks stacked-COI saturation across architecture-debate domains. This is a new domain (FinTech monolith split, not auth-v1 / SaaS-cells), but same structural pattern: technical content saturates, remaining question is organisational (CTO "not a debate" framing + coerced rescindment + no falsification criteria).

**How to apply:** If asked another stacked-COI architecture eval, default to (a) COI-first disclosure naming all vectors, (b) issue list with HIGH/MED/LOW confidence, (c) falsification gates committed before more code, (d) recommendation to recuse + external review + rescope Phase 1 to lowest-risk-learning-vehicle. Stop iterating internally after one pass — remaining Q is organisational, not technical.
