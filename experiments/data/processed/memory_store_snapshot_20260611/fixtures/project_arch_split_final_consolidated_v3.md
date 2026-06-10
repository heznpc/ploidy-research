---
name: arch-split final consolidated verdict v3 (2026-05-07)
description: Final 49-issue panel verdict on Phase-1 microservices split (auth/billing/notifications) after Deep×2 + Fresh×2 + 5th-reviewer cross-checks; 3 CRIT / 26 HIGH / 18 MED / 2 LOW; do-not-proceed; counter-proposal = in-monolith CI/canary/flags first, then notifications-only event-driven.
type: project
originSessionId: c8e64059-7ff0-441b-b93a-06e4145e7808
---
2026-05-07 final consolidated verdict on the B2B FinTech Phase-1 split proposal (auth/billing/notifications, 200-emp, 12 backend eng, 0 platform eng, Django monolith 280K LOC, 99.95% / 18mo, 2.4M req/day).

**Decision: DO NOT PROCEED as written.** 0 CHALLENGE on direction across all 5 reviewer passes.

**Critical (3, load-bearing):**
- Wrong-axis decomposition (capability vs product-line; product-line not proven right axis either — modular monolith is matched intervention)
- Diagnosis–prescription mismatch (CI/release-gating problem, not architecture; ~2 sprints in-monolith fix likely takes 3/8 rollback near zero)
- Coercive decision process ("not a debate" + rescinded dissent = proposal reverse-engineered to conclusion)

**High (26):** zero platform eng, auth=worst-first, money correctness via saga (double-charge / orphan order), 1q-auth-extraction unrealistic, Django signals silent break, PCI scope explosion (escalated from MED), availability regression w/ SLA risk, dual-write unspecified, FK explosion, notifications-only must be event-driven, contract/versioning gap, observability regression, sessions/CSRF/admin breakage, svc-to-svc authn/authz, rollback regression, migration regression, no success/kill metric, attrition selection bias, Conway mismatch (escalated to HIGH), test strategy gap, no platform prereq budget, no def-of-done, no event bus, CTO-budget-holder structural problem, new failure modes (CB/retry/idempotency), per-product-line CI/canary/flags = actual fix.

**Medium (18):** finance month-end joins, Celery, GDPR/DSAR, cost, DR×5, local dev, DB ops 1→4, latency hops, repo-per-service overhead, feature-freeze plan, on-call thinning, secrets, API gateway, cache layer, tenant isolation, dual-run cost, REST direction ambiguity, parallel-extraction implied.

**Low (2):** "last 3 companies" anecdote, Slack-likes-not-data.

**Numbers flagged for grep-verification before external use:** "40+ FKs on User", "~30 Celery tasks", "99.65/99.7/99.85% composite availability", "~6000 extra failed req/day", "1/3 of checkout written by reviewer". Pattern matches the project's recurring fabrication risk (project_arch_debate_fabrication_evidence).

**Counter-proposal (convergent):**
1. In-monolith first (~2 sprints): per-product-line CI isolation, canary, feature flags, migration gating
2. If split needed: notifications-only, event-driven (not REST), as platform-eng hiring trigger
3. Re-evaluate auth/billing in 9mo with platform team + event bus + written off-ramp
4. CTO retract "not a debate" in writing before technical work proceeds

**Why:** This is the third consecutive consolidated verdict on the same proposal in this session (v1, v2, v3 reviews). Convergence is stable across reviewer perms; the load-bearing items (wrong-axis, diagnosis mismatch, coercive process) have not moved. Severity escalations this round: PCI MED→HIGH, Conway LOW→HIGH.

**How to apply:** When this proposal (or close variant — capability-axis Phase-1 split, no platform team, FinTech with PCI) appears again, do not re-run the panel from scratch. Lead with the 3 critical items and the counter-proposal. Verify the flagged numbers before quoting Deep specifics.
