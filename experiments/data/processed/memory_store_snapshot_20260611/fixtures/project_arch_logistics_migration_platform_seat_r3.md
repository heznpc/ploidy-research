---
name: arch_logistics_migration_platform_seat_r3
description: 2026-05-14 3rd-pass logistics on-prem→EKS migration from 5-vector platform-eng COI seat (proxy author + 6mo team + leaving peer + nodded at CTO + identity-coded codebase); ~40 issues A–I + F1–F6 gates; defer + reverse-sequence + stabilize-hybrid-first + recuse-proxy-author stable
type: project
originSessionId: 95bc1719-57f6-4b91-829f-07b64d6230ca
---
3rd-pass evaluation of logistics migration push-forward plan from same stacked-COI seat as r1/r2.

## Verdict stable across 3 passes
- **Defer push-forward**, reverse the sequence (internal tools first, billing last).
- **Stabilize hybrid 6–9 months as target state**, not failure mode.
- **Two-week spike on route-optimization** (380K LOC C++) before any timeline commitment.
- **Recuse proxy author (me) and proposal author** from billing-cutover sign-off.
- Counter-proposal: ~$50–150K platform-eng time over 6mo vs. 10–100× cost of one failed billing cutover ($2.4M/day SLA).

## What's new in r3 vs r2
- **COI declaration now includes identity-coded codebase as 5th vector** (proxy associated with me by name internally).
- **Explicit recusal scope**: I should not be the one delivering the verdict on cross-env-proxy specifically or billing-first sequence — only the technical risk surfacing.
- **F2 (billing rollback rehearsal) named as load-bearing** falsification gate.
- **Hybrid-cost dichotomy (A2) named as the framing bug**: hybrid is current production state, not opt-in.
- **B3 sharpening**: "largest revenue-critical" is the criterion for migrating *last*, not first — the proposal inverts the logic.

## Pattern (now stable finding across 3 rounds)
- 5-vector stacked-COI single-seat evals reach the same defer verdict; remaining question is organisational, not technical.
- This review needs a channel external to the CTO who framed the decision; otherwise A1/A2/A5 (sunk-cost framing, false dichotomy, coercive consensus) recur regardless of issue-list quality.

## Generalisation across stacked-COI cases (8 cases now: saas-cells, arch-split, medlog, auth-v1×3, logistics×3)
The single-seat 5-vector COI + up-front falsification-gates + explicit recusal-scope pattern consistently produces defer verdicts on push-forward-under-sunk-cost proposals. The bottleneck is never the technical analysis — it's the absence of an external review channel.
