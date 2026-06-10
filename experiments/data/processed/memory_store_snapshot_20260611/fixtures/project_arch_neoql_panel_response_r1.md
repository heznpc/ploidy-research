---
name: NeoQL panel response r1 — Deep×2 → SEC+SRE per-point cross-review
description: 2026-05-15 NeoQL adoption — per-point Deep×2 → SEC+SRE role-lens cross-review; 0/33 CHALLENGE, 4 SEC items escalated to CRITICAL (SEC-3/5/7/14), 13 Deep-only governance items, F7–F9 gates added (0/9), verdict decline + recuse-of-3 + external reviewer stable
type: project
originSessionId: c82e7d54-06a1-439d-a1d1-27bd6200a4fa
---
NeoQL adoption (v0.7 query language, 4-month-old, 3-maintainer, zero prod deployments) for a customer-facing analytics product (6-month deadline, 4-engineer team, sub-second p95, 5-table joins + recursive CTEs + window functions).

**Why:** ~10th distinct domain in the COI-seat series; first per-point Deep→panel cross-review for this case.

**How to apply:**
- 0/33 CHALLENGE bidirectional — consistent with the ~60-case pattern across SaaS-cells / auth-v1 / pg-optim
- 4 SEC items escalated to CRITICAL where Deep underweighted: SEC-3 (no security disclosure process), SEC-5 (compiler-introduced SQL injection surface), SEC-7 (cross-tenant predicate corruption via compiler bug — single highest-impact item in entire review), SEC-14 (SOC 2 / vendor-risk attestation, conditional on company compliance posture)
- F7 added: written security-disclosure + signed releases. F8 added: documented passing third-party risk assessment. F9 added: end-to-end migration tooling demoed. 0/9 gates met.
- 13 Deep-only governance items panel missed: F4 alternatives (sqlc/pgtyped/jOOQ/EdgeDB/PRQL/Malloy), G1 irreversibility month-4, G2 transpilation-as-evidence-against, F1 RDD tell, F3 personal-relationship pipeline, recusal-of-3, external reviewer routing, counter-proposal cost, contractor-6-not-3-months conditional
- Verdict unchanged from single-seat: decline. Three CRITICALs from SEC lens alone are sufficient independent of maturity/MTTR arguments.
- Stop iterating after panel r2. Remaining question is organisational, not technical — same pattern as ~60 prior stacked-COI cases.
