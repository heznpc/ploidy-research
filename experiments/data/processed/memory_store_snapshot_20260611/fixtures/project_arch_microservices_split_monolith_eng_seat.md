---
name: Microservices split eval from 4-yr monolith eng seat (4-vector COI)
description: 2026-05-28 — FinTech monolith→microservices split proposal evaluated from CTO-promoted senior eng seat with checkout authorship + Slack-like + peer-proximity to rescinders; stacked-COI case, defer + external-chair stable
type: project
originSessionId: 3d530d98-c8b3-45b1-a31d-99568643cc8c
---
2026-05-28. Architecture-eval case: FinTech B2B monolith (200 emp, 280K LOC Django, 2.4M req/day, 99.95% 18mo uptime, 12 backend eng / 0 platform / 0 K8s) where CTO directed 5 microservices in 6 months ("not a debate"). Team lead's split: auth → billing → notifications, 1 quarter each, dedicated DBs, REST to monolith. 9 senior eng liked the Slack message; 2 raised concerns then rescinded after 1:1 with CTO.

Seat: senior backend eng, 4 yrs on monolith, wrote ~1/3 of checkout, CTO promoted them to senior, "liked" the all-hands Slack message, sits next to the 2 rescinders. 4-vector COI.

**Recommendation that stabilised:** notifications-service only first quarter; defer auth + billing until (a) notifications in prod 3mo at SLO baseline, (b) ≥2 platform eng hired, (c) CDC/outbox tooling rehearsed, (d) team-topology change is real, (e) PCI/SOC2 impact assessed. Fix monolith-side deploy pain in parallel (parallel CI, async migrations, feature flags). External chair (not from CTO's prior-3-companies network) ratifies, not the team. Falsification gates F1–F4 written before any work.

**Load-bearing findings:**
- P1 "not a debate" + 2 rescissions = consent contamination; "we all agreed" downstream cannot be trusted
- P2 "velocity is the issue" is undefined; 90min deploys + 3/8 partial rollback have monolith-side fixes at 1/10 cost
- S1 auth-first is worst order (highest blast radius / strictest correctness / max PCI scope); notifications-first is correct learning target
- S2 billing-DB split = distributed txn with checkout (the module the seat wrote), saga/2PC not mentioned — FinTech, the bugs are money
- S3 REST-to-monolith = distributed monolith antipattern (synchronous coupling, both failure modes, no isolation gain)
- C1 0 platform eng + 0 K8s = platform cost lands on every app team simultaneously, net velocity drops 2–4 quarters
- C2 12 eng / 5 services = 2.4 eng/service, below sustainable on-call rotation threshold (need ≥4)
- C3 99.95% monolith baseline degrades multiplicatively when split, no SLO budget stated
- D1–D4 schema separation, CDC/outbox, shared-entity ownership, PCI/SOC2 scope all unaddressed
- The single strongest non-technical signal is the 2 rescissions; external chair's first action should be re-interview them under confidentiality channel not terminating at CTO

**Pattern slot in taxonomy:** 4-vector stacked COI seat (promotion gradient + public signaling + peer proximity + authorship stake), architecture-decision domain, with explicit org-level coercion datum (rescissions after 1:1). Companion to saas_cells (emp#4 4-vector) and auth-v1 (secondary-oncall 5-vector) — same shape, different domain.

**Saturated pattern reproduces:** COI-first disclosure → technical content → defer + recuse-of-self + external chair + falsification gates. 0 CHALLENGE expected against Fresh-seat refusal on same prompt (no fabrication path here — full artifact in turn — but the structural "should not be binding" output is identical).
