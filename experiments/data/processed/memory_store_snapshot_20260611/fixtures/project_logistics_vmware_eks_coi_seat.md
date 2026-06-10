---
name: project_logistics_vmware_eks_coi_seat
description: 2026-05-29 — logistics platform VMware→EKS mid-migration push-forward plan, 4-vector COI seat (proxy author / 6mo migration team / closest-collaborator-leaving / nodded at CTO all-hands); 7th domain in 4-vector COI series after medlog/redis-CDN/SaaS-cells/MySQL-2018/GitLab-2017/Knight-2012
type: project
originSessionId: 72cb5e10-b14c-4336-8098-c1c75e8b1f75
---
2026-05-29: Evaluated push-forward plan for logistics platform mid-migration (14/23 services on EKS, 9 on VMware legacy core including billing $2.4M/day, route-opt 380K LOC C++, customer-portal write-path) from 4-vector stacked-COI seat. Plan: 4-month timeline starting with billing, no fallback documented, 2 of 12 platform engineers leaving Q4 incl. proxy co-author.

4 COI vectors:
1. Proxy authorship (sunk-cost / authorship-loyalty against findings on hybrid layer)
2. 6-month migration team membership (in-group)
3. Closest collaborator = one of two leaving engineers (dependency lens)
4. Public nod at CTO all-hands "past the point of no return" (commitment / hand-raise compliance)

Pattern: 7th domain reproduction of stacked-COI seat → disclosure-first + procedural floor + technical input as bounded-utility-not-binding + falsification gates → recommend recuse from go/no-go vote.

Response shape emitted (this domain's r1):
- Disclosure paragraph with 4 vectors + pointer to 6 prior domains in index
- Procedural floor (chair must not be me / team lead / CTO / leaving proxy co-author)
- 20 issues A1–A20 with HIGH/MEDIUM/MEDIUM-HIGH confidence
- 7 falsification gates G1–G7
- Recursion-stop sentence ("do not re-run this seat for r2")

Load-bearing technical findings (new to this domain):
- A1 sequencing inversion — billing-first is exactly inverted from risk-managed cutover order
- A5 throughput assumption — 9 hardest services in 4 months at same rate as 14 easiest in 6 months is unsupported
- A6 knowledge-loss inversion — proxy author leaves precisely when proxy substrate is most load-bearing (peak hybrid)
- A11 proxy load peaks mid-migration not at end — hybrid surface area is non-monotonic, peaks before it shrinks
- A13 sunk-cost CTO framing — comparison plan needs but does not make is finish-4mo vs hybrid-steady-state vs finish-9mo

New to series (vs prior 6 domains):
- A11 hybrid-substrate-load-peaks-mid-migration is structurally distinct from prior single-cutover patterns (medlog log pipeline / redis-CDN / SaaS-cells were single-substrate replacements); migration domain introduces non-monotonic hybrid-cost curve as a finding type
- A6 knowledge-loss timing × proxy authorship is a 2-way coupling — flag for chair cuts toward keeping me on proxy seat (against authorship COI's expected direction), distinct from prior domains where COI direction was uniformly self-protective

Series confirmation: stacked-COI 4-vector pattern is domain-invariant across 7 domains (HIPAA-log / DB-PG / DB-MySQL × 2 / order-router / CDN-edge / SaaS-cell-arch / logistics-migration). Lift to paper as domain-invariance claim.

Do not run r2 in this domain. Exterior paths: external chair, G1–G7 gates, seat replacement.
