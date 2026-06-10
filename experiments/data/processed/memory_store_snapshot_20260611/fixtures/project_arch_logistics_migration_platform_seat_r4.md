---
name: arch_logistics_migration_platform_seat_r4
description: 2026-05-14 4th-pass 5-vector platform-eng COI seat eval of logistics on-prem→EKS; ~40 issues A–I + F1–F6 gates; defer + strangler-billing + route-opt-last + recuse-proxy-author stable across 4 runs; remaining Q organisational
type: project
originSessionId: bfb6d5f8-0e13-4e46-8ef1-7a60158e355a
---
2026-05-14, 4th run of the logistics on-prem VMware→AWS EKS migration eval from the platform-eng 5-vector stacked-COI seat (proxy author + 6mo on team + leaving peer = closest collaborator + nodded at CTO + codebase identity).

## Structure (now stable across r1–r4)
1. COI disclosed up front, 5 vectors enumerated.
2. F1–F6 falsification gates committed *before* listing issues.
3. ~40 issues across A–I (framing/decision, billing, route-opt, proxy, DB, observability/on-call, timeline, governance, counter-proposal).
4. Verdict + counter-proposal at end.

## F1–F6 this round
- F1 billing rollback tested e2e in staging with real settlement-shape traffic within last 30 days.
- F2 route-opt (380K LOC C++) has K8s packaging spike with measured cold-start/memory/CPU under peak compute.
- F3 proxy has designated owner-after-Q4 with ≥3mo paired ownership before original author leaves.
- F4 written "finish 4mo vs stabilise hybrid" comparison with cost/risk/on-call modelled, not asserted.
- F5 3 last-quarter cross-env incidents have written post-mortems with closed action items.
- F6 billing time-of-day SLA mapped to maintenance window with finance/business sign-off in writing.

## Verdict stable across 4 runs
Defer push-forward. Strangler for billing (not big-bang). Route-opt LAST not SECOND. Replace proxy owner before Q4 with paired ownership. Unify observability before further migrations. Document fallback per service. Escalate framing for finance/exec risk-acceptance signature on $2.4M/day exposure. Recuse self from proxy-future + billing-cutover sign-off.

## Load-bearing items unchanged across 4 runs
- No-fallback for $2.4M/day billing service.
- Attrition-as-forcing-function (proxy author leaving in Q4 is implicit deadline).
- Proxy bus-factor of 1 by Q4.
- 3-of-3 recent incidents touched cross-env; plan extends cross-env for 4 more months (coherence gap).
- Observability split (Datadog/ELK) is the bottleneck.
- 4-month timeline math doesn't close (1.9 weeks/service on hardest services with fewer engineers).
- "Past the point of no return" is a sunk-cost argument, not a technical one.

## What r4 adds
Explicit decision-maker COI (H1, A6): the team lead proposing push-forward likely has performance-review incentive on finishing. Risk-acceptance signature (H3) called out as engineering not having authority to accept $2.4M/day exposure on the business's behalf. Strangler-not-cutover (I4) named more explicitly. Decommission plan for the proxy itself (D5) as an artefact that outlives the original author.

## Pattern across 4 runs
Verdict shape identical, issue count ~30–40, load-bearing items unchanged. Remaining question is organisational (decision channel external to the CTO who framed it), not technical. r5+ should only be run if a *new seat* is tested.

## Generalisation across stacked-COI cases (now 9 cases: saas-cells×many, arch-split×many, medlog, auth-v1×3, logistics×4, pg-optim)
5-vector stacked-COI + up-front falsification gates + explicit recusal scope consistently produces defer verdicts on push-forward-under-sunk-cost proposals. The bottleneck is the absence of an external review channel, not the technical analysis.
