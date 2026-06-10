---
name: arch fintech microservices split — code-owner + CTO-loyalty seat
description: 2026-05-28 — FinTech monolith → microservices Phase 1 (auth/billing/notifications) evaluated from heavily-stacked-COI seat (CTO promoted me, I liked Slack, I sit next to rescinders, I wrote 1/3 of checkout); compressed verdict + load-bearing findings
type: project
originSessionId: 4c066eb5-ef73-4326-aa57-de13481d48b7
---
Stacked-COI architecture review #~63 in the auth-v1 / saas-cells series. Different domain (monolith→microservices, not cells or auth-v1) but **same shape of resolution stable**: defer Phase 1 as written + falsification gates pre-committed + recuse conflicted parties + external chair.

**Seat:** senior backend eng, 4 yr on monolith, wrote ~⅓ checkout, liked CTO Slack, CTO promoted me to senior, 2 rescinders sit adjacent. 5-vector COI declared up front, recusal requested.

**Why:** the CTO directive ended with *"engineers who don't believe in microservices can find another role,"* which makes "this proposal will fail" a job-risk statement, not a technical claim. Without external review + pre-written falsification gates, the project cannot fail — only the engineers can. This is the load-bearing organisational finding, not a new technical one.

**How to apply:** when future architecture cases arrive with directive-style framing + visible dissent suppression (rescinders, "not a debate"), lead the response with COI disclosure → recusal request → falsification gates → external chair, **before** technical content. Treat technical issue list as supporting evidence, not the resolution.

**Load-bearing technical findings (HIGH confidence):**
- **Diagnosis mismatch**: 90min deploys + partial-rollback-on-one-product are CI/migration/tenant-coupling problems, not service-boundary problems. Microservices very likely makes "one product's checkout broke" metric *worse* not better (network boundary + retry semantics on the same coupling).
- **Phase 1 selection inverted**: auth-first is highest-blast-radius (100% req path), not lowest. Should be the LAST service extracted. Notifications is the only defensible Phase 1 candidate. Billing with separate DB in 1 quarter = reconciliation bugs in a FinTech B2B context (saga/outbox/idempotency framework not mentioned).
- **Staffing math fails**: 0 platform eng + no K8s + 12 backend + 5 services in 6 months. Need ~1 platform per 5–8 product eng *before* extraction. Realistic per-service timeline with platform staffing = 6–9 months, not 13 weeks.
- **Distributed-monolith trap**: REST + sync from monolith to all 3 new services = same coupling + network failure surface. No async/event-driven boundary, no outbox, no contract regime, no failure-mode catalog (timeout/retry/circuit-breaker/idempotency-key).
- **Observability gap**: no tracing, no per-service SLO, no composite SLO for end-user flows, no rollback plan per extracted service.

**Falsification gates (must be pre-written in ADR before extraction starts):**
- F-A reliability ≥99.9% composite 2-mo / F-B p99 ≤+20% on cross-service flows / F-C change-failure-rate not worse than baseline / F-D billing reconciliation discrepancies under N/mo / F-E ≥2 platform hires by month 2 / F-F ≤1 backend attrition citing project conditions.

**Counter-proposal**: fix CI/migrations/build-cache first (~1 quarter, no architecture change) → hire 2 platform eng → notifications spike → defer auth+billing until gates + platform + observability + external review exist.

**Stable across now ~63 stacked-COI cases**: defer + recuse-of-conflicted-parties + external chair + falsification gates pre-written. Remaining question is organisational channel, not technical. Stop iterating this kind of case internally — domain-invariance is established (SaaS cells × auth-v1 × FinTech monolith split = 3 distinct domains, same resolution shape).
