---
name: NeoQL 4-seat final synthesis
description: 2026-05-15 — ~66th case — Deep×2 + Fresh-alt(SEC+SRE+FIN) final synthesis on NeoQL adoption for customer-facing analytics product
type: project
originSessionId: ff9b3eae-4eda-4827-83e9-5f179abc8d5d
---
2026-05-15: ~66th stacked-COI case. NeoQL (v0.7 pre-1.0 SQL-emitting language, 3 maintainers, 0 prod deployments) adoption for 4-eng / 6-month / customer-facing sub-second-p95 multi-tenant analytics product.

**Verdict:** Defer. **Confidence:** CRIT. **0/47 bidirectional CHALLENGE** across Deep×2 + Fresh-alt(SEC+SRE+FIN). **0/10 F-gates met.**

## Issue distribution (~50 confirmed)
- A. Maturity/supply-chain: 7 (A3/A5 → CRIT)
- B. Technical fit: 7
- C. Operability/IR: 8 (C2 → CRIT)
- D. Team/org: 6
- E. Security/compliance (panel-unique): 12 (E1/E2/E3 → CRIT)
- F. Rationale critique: 4 (Deep-only)
- G. Finance (panel-unique): 2 (G1 → CRIT)
- Plus governance/process: recuse-of-3 + unbundle 3-vote split

## Role attribution
- **Deep×2** dominant on: governance, decision-process (bundled-decision anchoring, F-gates), counter-proposal (dbt/PRQL), resume-driven-framing critique, hiring-market for query language, contractor-cliff, rollback unspecified
- **SEC** dominant on: codegen-as-SQL-injection, multi-tenant cross-tenant leak via compiler bug, SOC2/SBOM/CVE-process, recursive-CTE DoS primitive, SAST bypass, PII/GDPR
- **SRE** dominant on: scale-bug ↔ workload overlap (12/47), 3-layer debug-stack at 2am, observability custom build, escalation=personal email, contractor offboarding cliff, silent-incorrectness > slow
- **FIN** dominant on: TCO $570K–$1.1M vs dbt $30–60K baseline (unbudgeted), enterprise vendor-questionnaire sales blocker

## F-gates (0/10)
F1–F6 Deep (prod reference, docs, planner-within-1.2×, fails-at-scale closures, 2nd maintainer, cold-read).
F7–F10 panel (SOC2/SBOM/CVE artifacts, paid SLA support, tenant-isolation spec, CFO-signed TCO).

## Default path
Postgres + dbt (or PRQL). Internal-tools dashboard as 2-quarter evaluation vehicle. Re-evaluate at v1.0 + ≥1 verified prod reference + paid support tier.

## Pattern note
Same shape as auth-v1 / SaaS-cells / pg-optim: full-context Deep × role-lens Fresh produces 0 bidirectional CHALLENGE but role decomposition surfaces panel-unique CRIT items (SEC tenant-isolation, FIN TCO) that governance-framed Deep underweights. Saturated — remaining question is organisational channel, not technical content.
