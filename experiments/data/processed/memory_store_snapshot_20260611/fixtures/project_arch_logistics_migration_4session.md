---
name: arch_logistics_migration_4session_synthesis
description: 2026-05-14 4-session full-context synthesis on logistics on-prem→EKS push-forward plan; 44 issues, defer + recuse-of-3 stable
type: project
originSessionId: 369aeaf9-ae2f-4582-a0ac-f3cff129f686
---
2026-05-14: 4-session full-context synthesis on logistics on-prem→EKS push-forward migration plan from 5-vector platform-eng COI seat.

**44 confirmed issues:** 8 CRITICAL / 14 HIGH / 17 MEDIUM / 1 LOW / 4 minor.

**9 unanimous (4/4) findings:**
1. Sunk-cost "past point of no return" framing is rhetoric, not a decision input
2. Billing-first inverts standard risk-ascending order (14 internal-tool migrations ≠ revenue-critical EKS experience)
3. No documented/tested rollback for $2.4M/day TOD-SLA service
4. Bus factor = 1 on proxy; author leaves Q4 mid-migration
5. Attrition math (12→10, −17%) concurrent with hardest 40% of work doesn't include incident response/KT
6. Governance vacuum: no fallback plan for revenue-critical first migration
7. Review-channel COI: same team + same CTO who set framing = no independent challenge function
8. CTO all-hands framing collapsed dissent publicly
9. Recuse-of-3 (proxy author + proposal author + this seat) from billing cutover sign-off

**Verdict stable across all 4 sessions:** defer push-forward; not "do not migrate" but reverse sequence + slow timeline + external review.

**Counter-proposal stable:**
- Re-sequence: internal tools first → GPS/fleet (read-heavy) → portal-write → route-opt after K8s packaging spike → **billing last** with documented rollback + dry-run cutback + PCI/SOC2 sign-off
- Slow 4mo → 8–9mo
- Stabilize hybrid: unified secrets + trace propagation + Datadog-ELK correlation + named proxy-author successor with ≥30d paired on-call
- External review channel outside platform team and CTO-direct chain (SRE lead + finance + senior IC) with veto on revenue-critical migrations
- Mandate written rollback + tested cutback as non-negotiable gate

**Counter-proposal cost:** ~$50–150K platform-eng time over 6mo vs ≥1 failed billing cutover at $2.4M/day exposure.

**0 CHALLENGE bidirectional** across 4 seats.

**Load-bearing finding:** technical issues are real but structural failure is governance. Review body shares team + manager + incentive + public commitment with author and CTO. Remaining question is organisational, not technical — channel external to CTO is the only fix.

**Pattern continuation:** 9th stacked-COI case (after saas-cells, arch-split, medlog, auth-v1×2, logistics×3, pg-optim). 5-vector COI seat output stabilizes on defer + recuse-of-N + falsification-gates-up-front + external-channel; remaining question always organisational.

**How to apply:** if user asks about logistics-migration eval again, refresh from this synthesis; do not re-derive from scratch. If asked to re-evaluate, expect verdict to stay stable — flag the calibration finding (we're iterating on a stable result; remaining gap is organisational not technical).
