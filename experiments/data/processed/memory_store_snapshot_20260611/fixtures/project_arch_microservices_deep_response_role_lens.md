---
name: arch microservices split — Deep response to SEC+SRE role-lens panel
description: 2026-05-14 ~55th stacked-COI/role-lens case — Deep×senior-backend 5-vector COI per-point on SEC+SRE Fresh-alt panel for monolith→microservices split; 0 CHALLENGE bidirectional; F7/F8 added; 6 net-new adoptions
type: project
originSessionId: 71005c89-efdc-4cc6-b6ae-b5f3a1029286
---
Context: monolith→microservices split, FinTech B2B, 280K LOC, 12 backend eng, 0 platform eng, 6-month directive from CTO with "not a debate" framing + 2 rescinded dissenters. Deep seat carries 5-vector COI (artifact author, reporting line, public Slack like, adjacent to rescinders, 4-year sunk cost).

## Per-point result (Deep on SEC+SRE)
- **0 CHALLENGE bidirectional** (~55th case in the stacked-COI/role-lens dataset, 9 domains)
- ~85% overlap with Deep's prior issue list

## F-gates after cross-review
- F1 — <20% cross-domain change frequency over 12mo postmortems
- F2 — deploy-time root cause is migrations+smoke (not compile/test)
- F3 — 3/8 rollback root cause is shared-table schema (not release hygiene)
- F4 — 2 senior platform engineers hired + sign off within 90d
- F5 — <5 cross-domain ACID transactions in checkout/auth/billing
- F6 — paid external review by non-CTO-chain senior architect
- **F7 (new, from SRE #11)** — per-service SLO targets whose composite ≥99.95%
- **F8 (new, from Sec #17)** — STRIDE/data-flow threat model for auth-service-as-extracted before commit

## Net-new adoptions from role-lens panel
- Sec #3 — TOCTOU + stale-permission + fail-open on AuthN/AuthZ split ambiguity
- Sec #6 — notifications-service as phishing/SSRF/template-injection vector
- Sec #12 — cross-DB PITR coherency (billing record exists, auth user does not)
- Sec #14 — input validation drift across services
- SRE #14 — DB operations triple (backup verify + PITR test + failover drill per DB)
- SRE #23 — no on-call training plan (separate from runbook gap)

## Deep-only items role lenses did not surface
- K1a–K1e cheap-fix alternatives (parallel CI, decoupled migrations, feature flags, modular monolith, per-product test selection)
- K2 — 3/8 rollbacks point to single-team release hygiene, not 280K-LOC architecture
- K3 — 280K LOC is not large (Shopify/Basecamp/GitHub-pre-microservices anchors)
- A2 — "did this at my last 3 companies" is unfalsifiable (selection bias)
- C5 — checkout-stays-in-monolith-while-its-deps-extracted = worst sequencing
- Recusal-of-3 structural recommendation (CTO + 2 rescinders + this seat)
- Counter-proposal at ~$30–60K, 8–10 weeks (diagnostic spike + external review + cheap-fix sprint + decision gate)
- Availability composite math: 99.95%⁴ ≈ 99.80% = ~3.5× more downtime
- Opportunity cost ~3–6 FTE-quarters lost
- Stop-condition: escalate outside CTO reporting line if F1–F8 not run

## Verdict (stable)
Defer split as proposed. Diagnose first. Decompose decision. Recuse 3 actors from load-bearing vote. ~$30–60K, 8–10 weeks counter-proposal. F1–F8 as commit gates.

## Pattern position
- ~55th stacked-COI/role-lens case in dataset; 9 domains
- 0 bidirectional CHALLENGE
- Stable finding: issue list reliable, single-seat verdict not — falsification gates + external review (outside CTO chain) load-bearing not optional
- Stop iterating internally; remaining Q is organisational channel (board/audit/external advisor)
