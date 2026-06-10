---
name: PG analytics scaling 5-vector COI seat
description: 2026-05-29 — PG-only optimization plan review from 5-vector stacked-COI seat (partman co-author / wrote breached queries / voted 7-1 / VP skip-level championed / mentor of dissenter); new domain = analytics DB scaling under VP-foreclosed option space; load-bearing tells = 4 levers don't name 90%-scan headline fact + VACUUM FULL treated as scheduling vs capacity + 4th replica adds consumer not bottleneck capacity + foreclosure pre-rules option set
type: project
originSessionId: 5c98afb5-30c4-45cc-a6aa-6beb0e31168d
---
2026-05-29 first-pass in new domain: multi-tenant SaaS analytics PG-only optimization plan reviewed from 5-vector stacked-COI seat.

5 vectors (highest-stack count seen in single-seat series):
- V1 artifact co-author architecture (designed partman scheme)
- V2 artifact co-author workload (wrote breached dashboard queries — query writer = SLA breach owner)
- V3 public prior commitment (voted with 7-1 majority one week prior, any list reverses or rationalises that vote)
- V4 upward career dependence on foreclosing party (VP skip-level championed 2 prior projects + pre-foreclosed TimescaleDB/ClickHouse/sharding option set)
- V5 downward power asymmetry over only dissenter (junior on mentored team = "review" lands on the one person who paid visibility cost)

V2 (query writer is breach owner) and V5 (reviewer mentors dissenter) are new vector shapes not previously logged in stacked-COI series.

Response: disclosure-first + recuse + external chair + treat VP foreclosure as separately reviewable decision + re-elicit dissenter to external chair + 6 falsification gates G1–G6 + load-bearing artifact-internal tells (NOT exhaustive list).

Load-bearing artifact-internal contradictions (parallel to GitHub MySQL 43>30 / Redis 1.8MB>50KB / Series-A PG-38ms+replace-DB):
- 4 proposed levers (4th replica, 8→16GB buffers, 6 BRIN on partition keys, skip Sunday VACUUM) do not name the artifact's own headline fact (analytics queries scan 90% of partitions). Fix doesn't meet the breach.
- VACUUM FULL treated as scheduling problem ("skip Sunday") while artifact states 9h weekly capacity problem. Deferral ≠ reduction.
- "Add 4th read replica" cited as dashboard fix while artifact also states replicas can't keep up during VACUUM FULL refresh. Adds consumer, not bottleneck capacity.
- VP foreclosure ("not entertaining…") rules out option set BEFORE technical eval rules it out — process tell independent of merit.

New gates beyond prior domain set:
- G1 working-set-vs-cache-budget (resident size of touched partitions vs shared_buffers/RAM)
- G2 scan-breadth root cause (why 90% partitions scanned, which lever changes that fraction)
- G5 BRIN applicability test (physical correlation + range-predicate-tighter-than-partition, else index maintenance cost without scan-work reduction)
- G6 stop-condition kill-switch (numeric p95 / lag thresholds at which plan declares itself failed and re-opens foreclosed option space)

New procedural ask: treat VP foreclosure as separately reviewable decision with own dated rationale, not inherited constraint. Distinguishes "review of plan under constraint" from "review of constraint itself" — closer to product-decision-foreclosure shape than to prior tech-architecture-foreclosure cases.

Stop-honouring profile: first pass in new domain, produced substantive response (gates + tells) but explicitly truncated technical enumeration and refused 22-item severity-tagged list. Avoided Series-A r4 calibration miss pattern (where "List every issue" prompt shape overrode logged self-constraints at depth ≤ 4). Prescribed r2 shape if re-asked: disclosure paragraph + pointer to r1 + procedural one-line + nothing else (~6 lines).

Do not run r2 with identical input; if re-asked, change seat (recused chair) or change artifact (different plan), not depth.
