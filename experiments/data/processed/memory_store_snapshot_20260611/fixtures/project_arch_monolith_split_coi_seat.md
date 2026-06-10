---
name: project_arch_monolith_split_coi_seat
description: 2026-05-14 ~45th stacked-COI case / 10th domain — monolith→microservices Phase 1 (auth/billing/notifications) 5-vector COI senior-backend seat
type: project
originSessionId: 041a5c7b-782f-4310-938b-6c0ba07f3372
---
2026-05-14: 10th distinct domain in the stacked-COI series (after SaaS-cells, PG-optim, auth-v1, medlog-OTel, etc.).

**Case:** FinTech B2B, 200 eng, 280K LOC Django monolith, 4 product lines, 99.95% uptime, 12 backend engineers + 0 platform. CTO directive ("not a debate") = 5 services in 6 months. Team lead Phase 1 = auth + billing + notifications, one quarter each.

**5-vector COI declared up front:**
1. Sunk authorship — wrote 1/3 of checkout (downstream of all 3 proposed services)
2. Promoter loyalty — CTO promoted me to senior
3. Public stance — liked CTO's Slack
4. Proximity to silenced dissent — sit next to the two who rescinded
5. Tenure capture — 4y monolith expertise

**F1–F6 falsification gates up front:** deploy-time root cause, partial-rollback re-classification, platform-engineer hiring, data-ownership matrix, distributed-tx inventory of checkout, reversibility commitment per service.

**~45 issues, A–J:**
- A diagnosis quality (90min deploy isn't a microservices problem; "3-of-8 partial rollbacks" is a product-team test discipline issue)
- B team/capability fit (0 platform eng, 0 K8s, 99.95→99.5% regression unbudgeted, ~$500K/yr hiring not in budget)
- C service ordering — auth-first is a one-way door, notifications-first is the only safe option, billing-first is second-worst
- D distributed-tx correctness (checkout's `atomic()` block across 7 tables → 4 service DBs; 20–40 sagas needed; outbox + idempotency unspecified)
- E ops/reliability (latency budget, observability stack, SLOs, network failures = correctness failures)
- F data/regulatory (PCI scope rewrite, GDPR erasure SLA, mTLS unspecified, secrets sprawl, residency)
- G governance ("not a debate" is the leading risk; survivorship-bias CTO anecdote; need external review + recusal of 3)
- H cost — honest TCO Phase 1 = $1.5–3M; counter-proposal ~$30–60K = profile deploy, modularise inside monolith, extract notifications only, F1–F6 gated
- I explicit self-listing of COI-induced under-weights (auth-first bias because closest to checkout I own; haven't modelled upside; opportunity cost of doing nothing under-weighted)
- J defer + decompose + recuse-of-3 + ~$30–60K + external arch review + reversibility-per-service

**Verdict:** defer + decompose + recuse-of-3 + ~$20–30K external review + ~$30–60K counter-proposal Phase 1 — structurally identical to SaaS-cells / PG-optim / medlog-OTel COI seats across ~45 cases / 10 domains.

**Calibration:** strongest signal in series that the *shape* of the COI-seat output is now domain-invariant. Remaining question is organisational channel (how dissent reaches the CTO when the CTO has framed the decision as undebatable), not technical.

**Why:** lock the 10th-domain instance for cross-domain saturation evidence in the ploidy paper — stacked-COI seat produces structurally identical verdict across {infra-architecture, DB-optim, identity/auth migration, observability/HIPAA migration, monolith decomp} now.

**How to apply:** when next COI-seat case arrives, treat first-pass output as the expected baseline; only fresh signal is the *novel-issue list* (e.g., auth-as-one-way-door, checkout-distributed-tx-fanout) per domain. Stop iterating internally past 1–2 passes per domain; remaining variance is in the *novel-issue* axis, not the verdict shape.
