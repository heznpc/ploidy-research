---
name: Migration push-forward Deep×2+Fresh×2 final verdict
description: 2026-05-08 — VMware→EKS push-forward plan (billing-first, 4mo, post-attrition); 45 issues (5 CRIT/24 HIGH/12 MED/4 LOW); 0 CHALLENGE bidirectional; do-not-approve, re-plan
type: project
originSessionId: 1bef4847-5e0c-44d5-a6d0-c85ac3bbb8e5
---
2026-05-08: Push-forward migration plan (9 services in 4 months, billing-first, 12→10 engineers, proxy author leaves Q4) Deep×2+Fresh×2+bidirectional+5th-Fresh review.

**Verdict: DO NOT APPROVE AS WRITTEN — re-plan, not tweak.** 0 strict CHALLENGEs in any direction.

**45 issues:** 5 CRIT / 24 HIGH / 12 MED / 4 LOW
- CRIT: rollback absent, billing-first inversion, proxy SPOF+author-leaving (escalated from HIGH on 5th-Fresh challenge to Deep's COI-anchored grading), financial reconciliation gap (Deep-only D2-12), abort authority (escalated F2-12)
- HIGH (load-bearing): route-opt 380K-LOC packaging under-scoped, route-opt-may-not-belong-on-EKS (Fresh-unique F1-13), capacity math infeasible (25–30% effective loss with KT overhead), velocity 2.3/mo→2.25/mo with harder services, DB topology absent, compute-EKS+data-VMware relocates hop into data path, observability MTTR↓×frequency↑, dependency graph ignored, proxy-needs-successor-not-hardening, sunk-cost framing, dual-run more expensive than hybrid

**Deep-unique catches (project context required):** proposer COI, attrition-as-coercion, customer-portal write-path consistency, GPS tail-latency under load, clock semantics (NTP/vDSO/hypervisor), financial reconciliation, PCI/SOX trail across proxy, permanent-hybrid for 4 internal tools, Q4 KT timing dependency, all-hands framing critique

**Fresh-unique catches (outside view required):** retire-not-harden proxy, route-opt may stay on dedicated infra, abort authority upstream of rollback, P50/P90 per-service deliverable, "midpoint not end" reframe, "static-capacity assumption" as load-bearing planning error

**5th-Fresh panel-wide gaps (M1–M10):** cumulative cutover-incident probability unmodeled (~37% across 9), 14-already-migrated not health-checked, irreversible state coupling once DB on RDS, feature-freeze policy missing, customer/regulatory communication missing, attrition-as-leading-indicator (not just capacity input), proxy-itself-in-PCI-scope, reverse-platform option (SaaS billing, dedicated route-opt, Tanzu/VCF) not considered, "done" definition missing, proxy-as-attribution-sink distorts incident root-cause

**Why:** Pattern matches prior arch-split + redis-CDN + fluentql cases — proposer COI + sunk-cost framing + no fallback + load-bearing-SPOF-by-leaver + capacity math infeasible + standard practice inverted. Fresh sees the framing/severity-floor; Deep sees the org/full-context tech (reconciliation, clock, PCI-trail).

**How to apply:** Reference when reviewing migration cutover plans, especially those with revenue-critical-first sequencing, key-person SPOF in transit infra, or "past the point of no return" framing. Pre-conditions for any billing work: rollback runbook + proxy succession-or-retirement + unified observability + DB topology + route-opt Phase-0 spike + dependency-graph sequencing + business-driver disclosure for deadline + abort authority + reconciliation plan + re-vote with proposer recused + health-check the 14 already-migrated.
