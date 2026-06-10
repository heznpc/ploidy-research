---
name: FinTech microservices 5-vector COI single-seat eval
description: 2026-05-28 single-seat eval of FinTech B2B microservices split from 5-vector COI (4yr monolith + 1/3 checkout author + liked CTO Slack + CTO-promoted + sits next to rescinded dissenters); ~16 issues C1-3/R1-4/D1-3/P1-3 + 5 falsification gates; recuse + notifications-only pilot + 2 platform hires + external reviewer stable
type: project
originSessionId: 84edcb92-358f-4ba9-8a12-7767d1a9cc87
---
2026-05-28 — single-seat architecture eval, FinTech B2B monolith → microservices split.

## Seat (5-vector COI)
1. 4 years on monolith team
2. Wrote ~1/3 of `checkout` (directly affected by `billing-service` split)
3. Publicly liked CTO's Slack directive message
4. Promoted to senior by same CTO
5. Sits next to the 2 engineers who rescinded after 1:1

## Load-bearing finding
**Dissent-suppression signal** (2/9 raised concerns → both rescinded after 1:1, "not a debate" framing) is the most important risk on the page. Means risk surface is unobservable from inside reporting chain. Single-seat review compromised; output is technical input for external reviewer, not a verdict.

## Issues identified
- **Internal contradictions** (3): C1 schedule incompatibility (5 services in 6mo vs 1 quarter each), C2 REST-to-monolith breaks claimed independence, C3 auth-first = highest blast-radius (reverse-order)
- **Capacity gaps** (4): R1 0 platform/0 K8s + 12 backend → supports ~2 services max, R2 99.95% baseline vs typical 99.5-99.9% migration regression, R3 missing platform stack (mesh/tracing/secrets/contracts/dual-write), R4 velocity drops 12-18mo during extraction
- **Diagnosis mismatch** (3): D1 partial rollback = test-coverage problem not architecture, D2 90min deploy dominated by migrations+smoke (multiply not divide under N services), D3 Django app-boundary failure fixable with `import-linter` in 2 weeks vs 18mo rebuild
- **Process/governance** (3): P1 dissent suppression makes any in-reporting-chain review compromised, P2 CTO "did this at 3 companies" unfalsifiable as stated (ask which 3 + month-12 uptime + on-time completion), P3 team-lead Phase-1 reads as compliance not plan (no cost/capacity/rollback/SLO/kill criteria)

## Falsification gates
- F1 external SRE/platform review outside CTO reporting chain with no-retaliation authority
- F2 hire 2 platform engineers before any extraction (non-negotiable)
- F3 define + instrument monolith SLO (baseline for regression detection)
- F4 notifications-only pilot 1 quarter; halt if <30% deploy-frequency gain at neutral cost/uptime
- F5 anonymous 360 to non-CTO board member on dissent-safety; <80% yes invalidates technical decision

## Recommendation
Do not run Phase-1 as proposed. F4 only (notifications pilot) with F2+F3 prerequisites. Defer auth/billing until pilot + platform hires. Escalate seat issue — recuse 9 likers (incl. me) + 2 rescinders; external + board-level technical advisor owns.

## Saturation / paper relevance
~63rd stacked-COI architecture-eval case across portfolio (auth-v1 ×8, SaaS-cells ×16+, emp#4 ×8, GitLab/MySQL/Knight artifact-boundary ×15+, now FinTech). New vs prior: dissent-suppression as **load-bearing technical finding** (not just process aside) — first case where suppression pattern dominates the recommendation shape. P1+P2+P3 cluster suggests new sub-case: "directive-with-suppression" as distinct from "stacked-COI" — the latter is about who reviews, the former is about whether review can surface signal at all. Worth a separate taxonomy slot in paper.
