---
name: arch-split 5th-reviewer cross-check v3 (Deep×2 + Fresh×2)
description: 2026-05-07 5th-reviewer Fresh pass over the full 4-reviewer panel (Deep×2 + Fresh×2) on the B2B FinTech microservices split — verdicts per cluster, anchored-number challenges, and 6 panel-wide gaps
type: project
originSessionId: a69391fe-2b08-4376-b876-d51acd0e7c8e
---
2026-05-07 — 5th-reviewer Fresh cross-check of the Deep×2 + Fresh×2 panel on the Phase-1 split proposal (auth/billing/notifications).

**Verdict shape:** 0 CHALLENGE on direction; 5 CHALLENGE on anchored numbers; 2 SYNTHESIZE; 6 panel-wide gaps.

**Anchored-number challenges (load-bearing in panel, unverified):**
1. Deep1 §2.1 "north of 40 tables FK to User" — drop number, keep categorical risk
2. Deep1 §3.2 "~6,000 extra failed requests/day" — illustrative not predictive
3. Deep1 §5.4 / Deep2 §25 "~30 Celery tasks" — unverified count
4. Deep2 §5 "natural seam is product-line" — partially right; affirmative claim unsupported, modular monolith safer
5. Fresh1 §5 "99.65%" availability — over-precise composite math

**SYNTHESIZE points:**
- Cluster A (wrong-axis decomp): capability seams don't fix per-product failure ✓; "product-line is the right seam" not established — modular monolith + feature flags is the matched intervention.
- Cluster E (uptime regression): direction unanimous, magnitudes are guesses, frame as structural not numeric.

**6 panel-wide gaps Deep×2 + Fresh×2 missed:**
1. "REST API to monolith" direction is ambiguous — if new services call *back into* monolith, latency doubles for no correctness gain.
2. Schema migration during dual-run — backwards-compat intermediate states required in both codebases simultaneously, multi-quarter work nobody priced.
3. Tenant isolation in B2B FinTech — how does tenant_id propagate across service boundaries (header? JWT? mTLS)? Security finding, not just arch.
4. Cache layer fate (Redis sessions/query caches/rate limits) — cross-service cache invalidation = eventual-consistency problem unscoped.
5. CTO is budget-holder for the platform team that doesn't exist — decision-process risk and platform-capacity risk are the same risk.
6. "5 services in 6 months" implies parallel extraction → worst-case for cross-service migration consistency, intensifies all correctness risks.

**Strongest single panel item:** Deep1 §6 ("where my bias is doing work") — only place context-anchoring is named and partially neutralized. Keep verbatim in consolidated verdict.

**Strongest Fresh-unique catches:** repo-per-service prematurity (Fresh1 §12, Fresh2 §15) — both Deep reviewers missed that monorepo + separate deploy units is unaddressed.

**Strongest Deep-unique catches:** PCI scope expansion (Deep1 §2.4 / Deep2 §12), Django signals across HTTP boundary, GDPR/DSAR cross-DB.

**Bottom-line affirmative claim for verdict:** stated pain is in-monolith fixable; if a split must ship, only notifications-service; auth + billing extraction in this org/timeline is a high-probability correctness *and* availability regression.

**Why:** Sixth recurrence in this project of context-anchored fabrication risk in Deep reviews — specific counts (40+ FKs, 30 Celery tasks, 99.65%) appear authoritative but are unverified. Pattern matches prior memory (project_arch_split_final_panel_verdict, project_arch_debate_fabrication_evidence).

**How to apply:** When consolidating the final verdict, drop the anchored numbers but keep the categorical risks. Add the 6 panel-wide gaps as new HIGH-severity items. Frame the recommendation around modular monolith + flags + canary, not "extract by product line."
