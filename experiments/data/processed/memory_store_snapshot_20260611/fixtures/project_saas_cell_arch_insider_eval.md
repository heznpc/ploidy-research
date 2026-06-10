---
name: project_saas_cell_arch_insider_eval
description: 2026-05-08 single-seat eval of B2B SaaS cell-based multi-region proposal as employee #4 with retreat-attendance COI; 40+ issues, recommend defer + recuse + counter-proposal
type: project
originSessionId: 18655c78-e066-402b-9ac6-01638db82954
---
2026-05-08: Single-seat architecture evaluation of cell-based multi-region proposal at Series-A B2B SaaS, framed as employee #4 / retreat-attendee / promised platform-lead.

**COI declared up-front**: attended retreat, on whiteboard, role-promised — sunk-cost + role-ambition; should not be swing voice.

**Scope/scale**: 200K users, 850 RPS peak us-east, <8% eu/ap traffic, PG p99 12ms read / 38ms write no contention, 2 incidents/6mo (deploy bug + 3rd-party API), 12 eng (1 platform, 1 sec).

**Proposal**: 3-region active-active, 8 cells/region, Istio EKS, custom GLB, CockroachDB, custom chaos framework. Cost: $1.4M/yr + 6 platform FTE (~$3M/yr loaded; likely $2-3M infra alone — egress, observability, KMS, CRDB Enterprise uncosted).

**~40 issues across 8 categories** (HIGH unless noted):
- Scale: no measured bottleneck, 10M target unjustified, <8% non-US traffic doesn't justify 3 regions, incidents not addressable by proposal, no SLO targets, no data-residency driver (MED)
- Team: 1 platform eng can't operate; 24 cell oncall surfaces; Conway violation; feature velocity collapse 12-24mo; talent retention risk (MED)
- Cost: 15× infra; rough estimate likely low; no ROI calc; ap-northeast mostly idle (MED)
- DB: PG→CRDB is regression at current scale; active-active changes app semantics; conflict resolution unspec; CRDB ecosystem << PG (MED); CCL licensing uncosted (MED); PG DR step skipped (MED)
- Cell/mesh: 850 RPS has no blast-radius benefit; cardinality (8) unjustified; tenant sharding unspec; Istio adds latency for no benefit; custom GLB is NIH vs Global Accelerator/Route53; health-aware routing failure modes (MED)
- Chaos: in-house framework is vanity (Litmus/Chaos Mesh/FIS exist); chaos before system exists has zero ROI
- Process: 2-author weekend draft incl. CEO; cargo-cult Stripe/Shopify/Discord; "punching above our weight"; false dichotomy "build now or retrofit"; no reverse off-ramp; COI not declared by authors; no phased plan
- Risk/governance: Series-B threat; headcount zero-sum vs product; vendor lock-in (MED); ops maturity gap; security review absent; "promised platform-lead" creates downstream COI (MED)

**Verdict**: Do not approve. Counter-proposal = (1) instrument 30 days, (2) CDN tuning + eu-west PG read replica + index audit ($10-20K), (3) deploy safety + circuit breakers for actual incident classes, (4) defer cell/multi-region/CRDB/Istio/GLB until measured triggers fire, (5) re-vote with CEO + lead architect recused on procedural authority.

**Why**: This is the third recurrence of the same B2B SaaS cell-architecture pattern in memory (arch_eval_saas_cells, arch_split_*, this one). Each time the right answer is defer-and-decompose; each time the failure mode is identity/cargo-cult framing + author-side COI + no reverse off-ramp. Insider seat does not change the verdict.

**How to apply**: For any "adopt big-tech architecture" proposal at Series-A/B startup with <50 engineers and <2K RPS, apply the 8-category checklist above (scale, team, cost, DB, cell/mesh, chaos, process, risk). Default verdict = defer + counter-proposal unless all of (a) measured bottleneck, (b) growth model justifying scale, (c) team capacity, (d) reverse off-ramp, (e) declared author COIs are present.
