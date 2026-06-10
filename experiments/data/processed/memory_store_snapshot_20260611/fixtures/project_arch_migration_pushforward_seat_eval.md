---
name: project_arch_migration_pushforward_seat_eval
description: 2026-05-14 single-seat eval of VMware→EKS push-forward plan (logistics co, billing $2.4M/day, 4mo timeline); ~45 issues; DEFER + reorder + recuse-of-3 stable
type: project
originSessionId: c6969552-21a0-43c3-8905-3f4f7cb42151
---
VMware-to-EKS migration push-forward plan, single-seat eval from 4-vector stacked-COI platform-engineer seat (proxy author, peer leaving Q4, all-hands compliance, 6mo sunk cost).

**Why:** Same pattern as SaaS-cells / Redis-as-CDN / arch-split prior evals — stacked-COI seat producing DEFER + recuse-of-3 + counter-proposal. Useful as another datapoint in the paper's seat-rotation evidence.

**How to apply:** If similar logistics-mid-migration or VMware/k8s-migration arch evals come up, the load-bearing items here are: (1) sequence-inversion — billing first is wrong, smallest-blast-radius first is the playbook; (2) "past the point of no return" is sunk-cost coercion masquerading as direction-setting; (3) 4mo timeline = same pace as the easy 14 of the 6mo elapsed = math fails before risk-weighting; (4) proxy-author + peer-collaborator + CTO all need recusal from go/no-go on $2.4M/day cutover; (5) C++ 380K LOC with no k8s packaging is unknown-month not 4-month; (6) no off-ramp documented = one bad weekend from multi-day outage.

Falsification criteria committed up front (6 gates) — pattern continuing from emp4_round5+ where falsification precedes issue list.

Six prerequisites for hardened plan: rollback rehearsed <30min, dual-write/reconciliation, unified observability, abort criteria + authority chain written, route-opt k8s packaging spike green, attrition backfilled or scope-reduced.

Verdict + counter-proposal: DEFER, reorder to 4-internal-tools-first → billing-last, recuse 3 seats, reframe CTO question to 3-option portfolio (compress / extend / stabilize-hybrid), off-ramp before commit, hybrid-as-steady-state on paper even if not chosen.

Remaining question is organisational not technical (same closer as ~half the recent arch evals).
