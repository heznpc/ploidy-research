---
name: arch-split promoted-senior stacked-COI seat eval
description: 2026-05-14 single-seat eval of Phase-1 microservices split from promoted-by-CTO senior monolith engineer seat (5-vector stacked COI); ~40 issues; defer + recusal-of-3 + counter-proposal stable
type: project
originSessionId: cf409753-39b8-491a-90d5-1966924232e1
---
2026-05-14 single-seat eval of the Phase-1 microservices split case from the **promoted-by-CTO senior monolith engineer** seat (4 yrs on monolith, wrote 1/3 of checkout, liked CTO's Slack post, sits next to the two rescinders).

**5-vector stacked COI declared up front:** sunk cost (checkout authorship) + promotion debt + public Slack like + proximity to rescinders + in-group with the 9 likers.

**6 falsification criteria committed before issues:** F1 platform team ≥3 hired first / F2 rollback root-caused as deploy-coupling not test-gap / F3 dual-run cost signed by Finance / F4 deadline decoupled from CTO calendar / F5 seam maps to actual team boundaries / F6 written off-ramp criteria.

**~40 issues across 8 categories:** Diagnosis (D1–D5, all HIGH — wrong root cause, wrong seam, 99.95% baseline ignored), Org/capability (O1–O6 — 0 platform engineers, 12 ICs/3 services unsustainable, coerced process), Auth-extraction (A1–A5 — Django request.user pervasive, session-store latency at 2.4M req/day, PCI scope expansion), Billing-extraction (B1–B6 — money correctness + saga/outbox in a team with no distributed-systems track record; **checkout author flag on B6 self-disclosed**), Notifications (N1–N3 — only reasonable candidate, do this *only* and stop), Data/consistency (C1–C5 — no event bus chosen, GDPR cross-system, no migration strategy), Operational (OP1–OP6 — 3×99.95% chained = 99.85% availability regression), Schedule/governance (S1–S6 — "5 services in 6 months" vs "3 in 9 months" inconsistent, coerced process, no success metric, attrition risk).

**Verdict:** DO NOT PROCEED. Counter-proposal stable across all prior arch_split seats: fix CI (1 q) → modular monolith (2 q) → notifications-only extract (1 q) → hire 3 platform engineers → decouple deadline from CTO calendar.

**Recusal ask:** recuse self + other two promoted-by-CTO seniors from go/no-go vote. Remaining question is organisational not technical.

**How to apply:** when invoked on this same case from a CTO-aligned/promoted seat, lead with COI declaration + falsification criteria *before* issues — that structure is what makes the seat's "no" credible despite the stacked bias. Verdict has now been stable across ~20 seats/rounds of this case.
