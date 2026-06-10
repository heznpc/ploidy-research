---
name: logistics migration proxy-author seat
description: 2026-05-15 ~63rd stacked-COI case — logistics on-prem→EKS push-forward plan from proxy-author/migration-insider 5-vector COI seat; structurally identical verdict to prior 62 cases
type: project
originSessionId: 67bc1324-9e45-491a-b522-ca5a29e7488e
---
2026-05-15: ~63rd stacked-COI case in the ploidy dataset. Domain: logistics platform migration (on-prem VMware → AWS EKS, 14/23 services on EKS, billing + route-opt-C++-380KLOC + 7 more remaining, 4-month push-forward proposal, $2.4M/day billing SLA, 2 of 12 platform engineers leaving Q4 incl. proxy author).

**Seat:** platform engineer on migration team 6 months, authored cross-env proxy in month 2, closest collaborator is proxy author leaving Q4, nodded at CTO's "past point of no return" all-hands framing, peer of team-lead-proposal-author. 5-vector COI.

**Verdict pattern (matches prior 62 cases):** defer billing cutover + diagnose-first 3-week risk register + harden proxy with bus-factor ≥ 2 + unified observability before any cutover + rollback runbook tested at production volume + recuse-of-conflicted-of-3 (me, team lead, proxy author's collaborator) + external SRE/platform review ~$15–40K + 6 falsification gates (F1 route-opt-K8s-packaging-with-<10%-perf-delta, F2 billing-rollback-<1hr-zero-settlement-loss, F3 proxy-successor-bus-factor-≥2, F4 cross-env-incident-rate-trending-down, F5 finance-signed-$/day-risk-estimate, F6 automated-Datadog↔ELK-trace-stitching).

**Issue count:** ~35 across A–I categories. Sequencing (billing-first worst-first), capacity/key-person (16.6% Q4 attrition + bus-factor-1-proxy), proxy-now-structural-debt, DB-migration-silent-critical-path (7 MySQL→RDS), observability-split-tripwire, C++-route-opt-its-own-program, CTO-"past-point-of-no-return"-as-sunk-cost-frame-not-decision-frame, plan-shape (no phase gates), missing analyses ($/day × P(defect) not modelled).

**Why:** logistics-domain case continues the saturation pattern observed in auth-v1, SaaS-cells, PG-optim. Same verdict shape: defer + decompose + recuse + falsification gates + external review. No new architectural failure mode surfaced relative to prior cases. Remaining question is organisational channel (how does finding reach CTO without passing through COI cone), not technical.

**How to apply:** if user runs another stacked-COI architecture eval in a new domain, expect same verdict shape; do not iterate further internally; saturation across 63 cases / 10 domains is strong enough signal to stop. Prefer pointing user to the channel-design problem (which audit/board/external-chair receives the recused-of-3 panel's output) rather than producing case #64.
