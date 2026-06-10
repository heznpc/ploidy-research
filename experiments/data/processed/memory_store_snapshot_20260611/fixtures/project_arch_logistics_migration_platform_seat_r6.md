---
name: project_arch_logistics_migration_platform_seat_r6
description: 2026-05-14 6th-pass platform-eng 5-vector COI seat logistics-migration; ~35 issues A–H + F1–F6 gates; defer + reverse-sequence + stabilize-hybrid-first + recuse-proxy-author stable; ~11th stacked-COI case, pattern is stable finding, remaining Q always organisational
type: project
originSessionId: 6ba15204-1d26-4f1a-8072-3f6bc834b2e9
---
6th-pass single-seat logistics on-prem→EKS evaluation from 5-vector platform-eng COI seat (proxy author + 6mo team + leaving peer = closest collaborator + nodded at CTO all-hands + codebase identity).

**Up front, before issues**: 5-vector COI declared + recusal recommendation (proxy author should not be deciding voice on proxy retirement window) + F1–F6 falsification gates committed (billing rollback rehearsed; route-opt K8s packaging spike merged; proxy knowledge documented + on-called without author's help twice; hybrid cost measured not asserted; per-service bottom-up estimates from engineers doing the work; documented "month 3 slips" branch).

**~35 issues across A–H**: sequencing (billing-first inverts risk gradient, route-opt is separate program not service #2), timeline (4 months asserted not derived; no Q4 attrition buffer; no per-service bottom-up), fallback (no rollback for $2.4M/day billing is load-bearing flaw; "past point of no return" is rhetoric), proxy (retirement tied to data not services; bus factor 1; already-active liability), observability (Datadog/ELK manual correlation unsustainable; no MTTR per env), data (7 services on VMware MySQL is real long pole; billing data migration is separate program; replication lag during time-of-day SLA cutover), route-opt (380K LOC C++ packaging program not migration step; latency parity unspecified), governance (CTO framing forecloses decision; no risk register; recusal not built in; finance not in room; no off-ramp).

**Verdict stable across 6 passes**: defer push-forward as proposed + reverse sequencing (internal tools first, customer-portal-write-path, fleet/GPS; billing as separate phase 2 program; route-opt as separate indefinite phase 3) + stabilize hybrid first ~6 months + recuse proxy author from proxy-retirement decision.

**Calibration**: ~11th stacked-COI case overall. Pattern is now stable finding: technical verdict stabilises in 2–3 passes; COI + falsification + recusal load-bearing; remaining question is *always* organisational (which 3 non-migration-team / non-CTO-direct-report people decide, what channel bypasses the all-hands framing). Stop iterating on technical merits, shift to organisational channel.
