---
name: PG analytics stacked-COI review (first non-SaaS-cells/auth-v1 case)
description: 2026-05-28 — first stacked-COI architecture review on a different domain (PG-only analytics, partman, dashboard p95 breach, VP framing constraint); 5-vector COI; finding patterns reproduce
type: project
originSessionId: 7794e973-d185-44e2-ade3-e442cb6b3828
---
2026-05-28: New case in the stacked-COI architecture-review series — *different domain* from SaaS-cells (multi-region cells) and auth-v1 (Auth0 migration).

**Domain**: multi-tenant SaaS analytics on PG16 (12K tenants, 8M events/day), partman monthly partitions, 4.8s dashboard p95 SLA breach 4 weeks running, 9h weekly VACUUM FULL.

**Plan reviewed**: +4th read replica, shared_buffers 8→16GB on replicas, 6 BRIN on partition keys, skip Sunday VACUUM FULL.

**Seat (5-vector COI)**: 3-yr backend eng / designed partman / wrote dashboard queries / voted with 7-1 majority / VP=skip-level past champion / dissenter on mentee team.

**Findings reproduced from SaaS-cells / auth-v1 series**:
- Plan does not address actual bottleneck (90% partition scan = no real pruning; rollups missing).
- Individual mitigations mis-specified (BRIN on partition key redundant; new indexes contradict VACUUM-FULL skip).
- Capacity model unstated for stated growth (+20% writes / quarter).
- Falsification criteria absent, success metric absent, items shipped together (un-attributable).
- VP framing constraint contains category error (Timescale is PG-extension, not migration off PG) — no one in the room flagged it.
- 7-1 with junior-mentee dissenter = high-risk dissent-dies pattern.

**Why this matters for paper**: Confirms the stacked-COI + framing-foreclosure pattern is **domain-invariant** — reproduces in (1) multi-region cells, (2) auth/identity migration, (3) PG capacity / partitioning. Three distinct architectural domains, same review-degradation pattern.

**Why:** Paper case-study collection needs domain diversity to defend against "this is a cells-only / auth-only artefact" objection. PG-DB-tuning is a 3rd structurally-different domain.

**How to apply:** When generating further stacked-COI cases for paper evidence, prefer new domains (frontend perf, ML training infra, mobile release process, regulatory compliance) over additional SaaS-cells iterations. Marginal evidence value of 17th SaaS-cells round is ~zero; first round in a new domain is high.
