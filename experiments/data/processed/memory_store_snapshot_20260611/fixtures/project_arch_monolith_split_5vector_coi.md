---
name: monolith→microservices split — 5-vector COI seat
description: 2026-05-28 — Django monolith → 3-service split (auth/billing/notifications) reviewed from 5-vector COI seat (checkout-authorship + tenure + public-like + CTO-promoted + neighbour-of-rescinders); ~30 issues A–G + 5 falsification gates; defer-Phase-1 + recuse-of-3 + replace auth/billing-first with notifications-only + 6-week diagnostic stable
type: project
originSessionId: 99cd6c7e-c89c-47f1-9600-d530cc736870
---
2026-05-28 — yet another stacked-COI architecture-review case in the long ploidy series (now well past 60 variants across SaaS-cells, auth-v1, GitLab DB, GitHub MySQL, Knight Capital, and now monolith→microservices).

**Seat**: senior backend engineer, FinTech B2B platform, 4yr on monolith, wrote 1/3 of checkout, 'liked' CTO's Slack on the day, CTO promoted them, sits next to both engineers who 1:1'd-and-rescinded.

**Proposal**: Phase 1 extract auth + billing + notifications (1 quarter each); separate DB + REST + deploy. 12 backend engineers, 0 platform engineers, no K8s, 99.95% monolith uptime, 2.4M req/day, 280K LOC Django.

**5 COI vectors named up front** (new combo vs prior runs):
1. checkout authorship sunk cost
2. 4yr tenure / identity attachment
3. public 'like' on CTO message — reversal socially expensive
4. CTO did the promotion to senior
5. neighbour to both rescinders + observed the 1:1-and-rescind dynamic firsthand

(3) named as the biggest single distortion on this specific seat — distinct from prior runs which were dominated by promotion-history or co-authorship vectors. The 'public-like-then-reverse' axis is new in the series and worth lifting to paper as its own COI sub-type.

**5 falsification criteria committed before issue list**:
- F1 platform-eng hire before extraction
- F2 written per-service rollback thresholds (p99 / error / MTTR / page volume)
- F3 written decision log with rescinders + external advisor independent positions
- F4 "5 services in 6 months" → "1 service, gated on F2 for 60 days"
- F5 distributed-transaction model written before first DB split

**Verdict**: defer Phase 1 as written. Replace with 6-week diagnostic:
- hire platform eng
- attempt monolith-level fixes for stated pain first (modular boundaries / per-product CI / feature flags / canary) — 2 weeks
- only if those fail to move the metric, extract notifications *first* (not auth, not billing) — lowest blast radius, lowest consistency coupling
- 60-day prod gate before Phase 2
- recuse-of-3 + external chair

**Load-bearing technical findings (new vs prior series)**:
- C1: auth-first is the *worst* possible choice (total-platform-outage blast radius, zero K8s/mesh, no rehearsed runbook) — sharper than generic "first extraction risky"
- C2: billing-first requires distributed-tx design *with* checkout (which the seat-holder wrote 1/3 of) — REST-is-not-a-consistency-model
- G1/G2: diagnosis may be wrong — "3-of-8 partial rollbacks, one product's checkout broke" is *insufficient inter-product isolation in the monolith*, fixable with modular-monolith + per-product CI gates without splitting runtime. The split is one solution, not obviously the cheapest. **This is the biggest gap in the artifact — no evidence monolith-level fixes were tried.**
- A1: "not a debate" + 1:1-and-rescind = load-bearing risk regardless of architecture; every technical item assumes this is fixed

**Saturation**: stacked-COI verdict shape (defer + recuse + external + falsification gates) now reproduces across:
- SaaS cells (~20+ rounds)
- auth-v1 vs Auth0 (~8 rounds + 6 panel rounds)
- monolith→microservices (this round)
- 3 unrelated domains, 3 unrelated company shapes — verdict shape is domain-invariant when the COI pattern is stacked + the "not a debate" governance pattern is present.

**Paper claim candidate**: the "public-like-then-reverse" COI vector — a participant who has *already publicly signalled support* faces a sharper asymmetry than one who stayed silent. Worth its own sub-type in the COI taxonomy; not previously named in the series.

**Stop iterating** — this case is saturated by the prior 60+. Do not run r2 unless the prompt shape genuinely changes (e.g., the artifact includes prior monolith-level remediation attempts, which would test G1/G2 differently).
