---
name: project_arch_split_final_synthesis
description: 2026-05-07 final Deep×2 + Fresh×2 + 2 cross-check synthesis on Phase-1 microservices split (B2B FinTech) — 50 confirmed issues, DO NOT PROCEED
type: project
originSessionId: 8b554fb5-d7c1-480d-a82c-dd2b99fa1bdc
---
2026-05-07: Final synthesis of Phase-1 microservices split proposal evaluation (B2B FinTech, 12 backend eng, 280K LOC Django monolith, 99.95% uptime, 0 platform engineers, CTO-mandated "not a debate" with rescinded dissenters).

**Why:** Builds on `project_arch_split_proposal_verdict.md` (4-reviewer Deep+Fresh) + `project_arch_split_deep_response.md` (Deep×2 cross-check). Adds 2 5th-reviewer passes (one Deep, one Fresh) producing final issue list and severity reconciliation.

**How to apply:** Reference for any future architecture-split debate skill output, especially Django/FinTech contexts. Counter-proposal pattern (modular monolith + notifications-only + platform-hire-first + 3mo measurement gate) is convergent across 6 independent passes.

**Final tally:** 50 issues — 1 CRITICAL, 25 HIGH, 21 MEDIUM, 3 LOW.

**Load-bearing CRITICAL:** Coercion-corrupts-input (unanimous 4/4). Every technical risk is downstream because surfacing them was just shown to be career-coded.

**Severity corrections during cross-check:**
- F1#10 sync-coupling=distributed-monolith: MED → HIGH
- D2#26 secrets management: LOW → HIGH
- D1#26 vs D2#15 latency: reconciled MEDIUM for critical paths
- F1#17 data residency: LOW → MEDIUM floor
- D1#25 service naming: removed (too tactical)

**Deep-unique catches Fresh structurally cannot make:** Django middleware (`request.user`, `@login_required`, CSRF), Permission/RBAC tables, ORM signals/post_save, Celery ownership, Django admin loss, warehouse/BI ETL break, webhook ownership, rate-limit middleware, GDPR cascade, data residency, capacity math (1Q×3 + 4 product lines × 12 eng infeasible), attrition forecast, DR coordinated PIT restore, local dev friction.

**Fresh-unique catches Deep missed:** internal CTO/team-lead schedule contradiction (5-in-6mo vs 1-per-quarter), feature flags as direct fix for partial-rollback pain, strangler-fig strategy unspecified, "what's missing from proposal" structural framing.

**No fabrication detected** in Deep sessions. Both Deep sessions explicitly self-flagged "I liked the message" coercion bias; conclusions not softened.

**Counter-proposal (convergent across 6 passes):**
1. Re-open decision — restore dissent conditions (load-bearing)
2. Fix actual pain: zero-downtime migration tooling, feature flags, canary, faster CI (1Q, monolith intact)
3. Modular monolith intermediate step, prove seams 3mo
4. Extract notifications-only as platform-learning vehicle
5. Hire 2–3 platform engineers before any second extraction
6. Pre-extraction blocking diligence: FK census, signal census, Permission audit, Celery ownership map, downstream-consumer inventory
7. Defer auth/billing until boundaries have held in production for 3 months AND platform team exists
