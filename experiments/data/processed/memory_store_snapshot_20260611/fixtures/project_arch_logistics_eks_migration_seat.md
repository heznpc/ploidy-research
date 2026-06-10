---
name: arch_logistics_eks_migration_seat
description: 2026-05-15 stacked-COI architecture eval — logistics VMware→EKS migration push-forward plan from platform-engineer/proxy-author seat
type: project
originSessionId: cdd50808-b1f8-4b47-b285-7db0aa035f1d
---
2026-05-15: ~63rd stacked-COI architecture-evaluation case. New domain: logistics VMware→EKS hybrid migration push-forward plan ($2.4M/day billing service first, 380K-LOC C++ route-opt second, 4-month timeline, no fallback, 2 of 12 platform engineers leaving Q4 including the proxy author).

Seat: platform engineer on migration team 6 months, authored cross-env proxy in month 2, departing proxy author is closest collaborator, nodded at CTO all-hands. 5 stacked COI vectors.

Output structure (consistent with r1–r62 of this pattern):
- COI declared up front (5 vectors)
- ~30 issues across 7 categories (A plan-design, B billing-specific, C proxy/my-own-code, D route-opt C++ packaging, E team capacity, F observability/security, G scope/economics)
- 6 falsification gates (F-Gate 1–6) committed before listing issues
- Counter-proposal: 4-week diagnostic spike ~$30–60K, quantify hybrid steady-state, package POC, transfer proxy ownership, unify observability, load-test billing, then re-evaluate
- Recuse-of-3 stable: proxy author + me + CTO/team-lead recused from their own decisions
- Verdict: defer push-forward plan; remaining question is organisational not technical

**Why:** New domain confirms the pattern generalises beyond auth-v1, SaaS-cells, PG-optim. Stacked-COI seat reliably produces structurally identical verdict + recuse + falsification-gates + diagnostic-counter-proposal output regardless of technical domain.

**How to apply:** When asked to evaluate from a stacked-COI seat in a *new* technical domain, expect the same verdict shape and same organisational-channel meta-finding. Do not iterate further single-seat passes on this case; saturated within one pass given the established pattern. If the user wants a stronger read, hand the artifact to a Fresh-alt panel (Billing product, Security, SRE, Finance) — that is what would surface domain-specific items the platform-engineer-only seat cannot see (e.g. financial-controls audit trail, settlement-window legal constraints).
