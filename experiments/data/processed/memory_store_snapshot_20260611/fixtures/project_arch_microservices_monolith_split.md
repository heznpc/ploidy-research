---
name: arch microservices monolith split COI seat
description: 2026-05-14 ~42nd stacked-COI case (9th domain monolith→microservices); FinTech B2B 12-eng/0-platform team; 6mo/5svc CTO directive; 5-vector COI seat; defer + Phase-0 + recuse-of-9-likers + external-review + reopen-directive stable
type: project
originSessionId: b437547e-8a79-420b-91a9-8e87e2a51360
---
2026-05-14: ~42nd stacked-COI eval case, 9th domain (monolith→microservices split).

**Seat**: senior backend, 4yr monolith, wrote 1/3 of checkout, liked CTO's Slack message, CTO-promoted, sits next to 2 rescinded dissenters. 5-vector COI: sunk-cost + authorship + public-position + career-patron + proximity-to-silenced-dissent.

**Output structure (matches medlog/PG/SaaS pattern)**:
- COI declared up front + 5 vectors named
- 7 falsification gates (F1 platform capability, F2 velocity root cause, F3 first-extraction p99/error budget, F4 saga design, F5 rollback exercised, F6 deadline vs SLO, F7 dissenter re-interview) committed *before* issue list
- ~40 issues across 8 categories A–H (staffing, architecture, ops, velocity-hypothesis, decision-process, cost, per-service, compliance)
- Verdict: **defer + Phase-0 (hire+OTel+module boundaries+deploy fix) + re-decide at day 90 + start with notifications not auth + reject 5/6mo deadline + recuse 9 likers + external reviewer + anonymous dissenter re-interview**

**Load-bearing catches unique to this domain**:
- G4 arithmetic gate: team-lead plan (1Q × 3 svc serial = 9mo) already contradicts CTO deadline (5 svc / 6mo); the contradiction itself should reopen the directive
- B1: auth-service is *worst* possible first extraction (every request hot path); proposal led with it
- B3/H4: distributed transactions across payment + billing in B2B FinTech raises regulatory completeness question, not just engineering question
- D2: "one product's checkout broke" partial rollback is *intra-monolith module isolation failure*, not a microservices argument — fix with feature flags + per-product canary
- D4: industry base rate is 12–18mo velocity *regression* during migration; proposal projects gain by mo 6
- E1/E3/E6: "not a debate" + 9-engineer like-cascade + 2 rescinded dissenters = silenced consensus; cheapest signal suppressed; anonymous external re-interview is the structural fix

**Verdict stability**: defer + Phase-0 + recuse + external-review pattern is identical to ~41 prior stacked-COI cases across SaaS-cells, PG-optim, medlog→OTel, auth-v1, etc. Pattern saturated; remaining question is organisational channel (how to reopen a CTO directive that punishes dissent), not technical.

**How to apply**: when a future stacked-COI architectural eval lands, expect this same shape. The seat output is now reproducible enough to be the control condition in the ploidy paper's COI experiments — the contribution is the *structure* (COI declared, falsification gates pre-committed, recusal explicit), not the issue list.
