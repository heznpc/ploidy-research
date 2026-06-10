---
name: PG-only SaaS analytics architecture review — 5-vector stacked COI seat
description: 2026-05-28 — Senior backend (3yr tenure) reviewing team-lead PG-only plan after VP banned non-PG options; 5 COI vectors (own partman+queries, voted 7-1, VP skip-level champion, mentor of dissenter, constraint frame pre-closed); 16 issues 4 CRIT/5 HIGH/5 MED/1 LOW + meta-finding; recuse + rewritten plan around bloat/query-shape + external chair
type: project
originSessionId: 2ddd33d5-841a-4127-bfcb-d9d0aed190a4
---
Case shape: PG16 multi-tenant SaaS analytics, 12K customers, 8M ev/day, dashboard p95 4.8s SLA breach 4 weeks, weekly VACUUM FULL 9h. Team-lead plan: +4th replica, shared_buffers 8→16GB, 6 BRIN on partition keys, skip Sunday VACUUM FULL. VP pre-closed answer space ("no TimescaleDB/ClickHouse/sharding").

Seat: 5 COI vectors stacked — (1) author of partman scheme + dashboard queries being indicted, (2) voted with 7-1 majority publicly, (3) VP is skip-level champion, (4) mentor of the lone dissenter, (5) constraint frame pre-closed before review.

**Why:** Architecture-review COI series now spans 60+ saturated variants (SaaS-cells r1–r16 + auth-v1 r1–r8). This case adds two new structural elements vs prior series:
1. The reviewer is the *author of the artifact being indicted* (not just an adjacent committer / co-author / on-call) — vector (1) is direct authorship of both the partman scheme AND the dashboard queries flagged as the root cause.
2. The VP explicitly *pre-closed the answer space*. The plan is rational inside the constraint; the constraint itself is the load-bearing decision and was never reviewed.

Vectors (3)+(4) reproduce the "panel members all share career exposure to the dissent path" pattern from auth-v1; (2) reproduces the public-commitment-reversal cost from SaaS-cells.

**How to apply:** When a future architecture-review case has author-of-artifact + VP-pre-closed-frame + dissenter-as-mentee, do not iterate further variants — saturated. Lift directly to paper as the canonical example of:
- Reviewer-as-author indicting own work via "scan 90% of partitions" being a query-shape problem the reviewer wrote
- Constraint-frame critique as the load-bearing finding (VP banned the actual answer space)
- Recusal-of-3 + external-chair pattern reproduces in 3rd architecture-review domain (after SaaS-cells multi-region, auth-v1 IdP migration)

Findings load-bearing:
- CRITICAL: skipping VACUUM FULL with no alternative is anti-correlated with goal; VACUUM FULL on partman tables is wrong tool (pg_repack + partition drop is right); BRIN-on-partition-key is redundant with partition pruning; "scan 90% of partitions" is query-shape problem requiring rollups, not infra tuning
- HIGH: 4th replica increases lag not throughput (single WAL pipe); single-primary write ceiling at +20%/qtr; tenant+events same cluster = noisy neighbor; autovacuum failing but plan doesn't touch it; long-running analytics queries block autovacuum (xmin holder) = likely actual bloat driver; no SLO / falsification criteria
- Meta: constraint frame was the load-bearing decision and was not reviewed; 1 dissenter (junior, on team I mentor) was the only structural seat that could have flagged this without COI

Recommendation: recuse from vote; rewrite plan inside VP constraint around bloat-cluster (#1, #2, #4, #8, #9); escalate write-ceiling + tenant-isolation to external chair with constraint frame reopened; written SLO + 60-day falsification gate before any infra money.

**2nd-session delta (2026-05-28, separate run):** Same case re-prompted, structurally identical output. Two small additions worth folding in:
- Explicit falsification-gate list F1–F5 (p95 < 2.5s; replica lag < 5min during VACUUM window; n_dead_tup on hot partitions not rising; new BRIN idx_scan ≥ 1% of seq_scan at 4 weeks else drop; zero customer-visible incidents from `ACCESS EXCLUSIVE` lock window). Sharper than the generic "60-day falsification gate" above.
- C2: VP's "PG expertise is strategic asset" justification undercuts itself — TimescaleDB is a PG extension with same wire protocol + same operational knobs, so the constraint is wider than its stated reason supports. The constraint deserves to be questioned on its own terms, not just on outcome grounds.
Saturation confirmed: 2 independent sessions same day produced the same COI-first + 4 mitigation-critique + constraint-frame-as-load-bearing shape. Do not run a 3rd variant.
