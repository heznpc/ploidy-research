---
name: arch_logistics_migration_platform_seat
description: 2026-05-14 — logistics on-prem→EKS push-forward plan eval from platform-engineer 5-vector stacked-COI seat (proxy author + 6mo on team + leaving peer is close + nodded at CTO + owns ops pain); ~38 issues A–L + F1–F6 gates; defer + recuse-of-self-from-proxy + reverse-sequence + stabilize-hybrid-first stable
type: project
originSessionId: 4f72a52e-bcc4-40f6-98b7-efe42cd25516
---
**Case:** logistics co. mid-migration on-prem VMware → AWS EKS, 14/23 done, 9 left incl. billing ($2.4M/day SLA) + route-opt (380K LOC C++, no K8s packaging) + 4 internal tools. CTO frame: "past point of no return, 4mo to finish." Team lead plan: billing first, then route-opt, then rest. 2/12 platform eng leaving Q4 incl. proxy author.

**Seat (5-vector stacked COI):** authored cross-env proxy (sunk cost) + 6mo on migration team + closest collaborator is leaving proxy author + nodded at CTO all-hands (consistency bias) + platform eng owns ops pain either way.

**F-gates committed up front:** F1 billing-SLA-window vs rollback-RTO; F2 route-opt 6wk packaging spike; F3 proxy SME bus-factor at Q4; F4 hybrid cost/mo quantified; F5 documented halt criteria; F6 published RCA on 3 cross-env incidents.

**Issues (~38 across A–L):**
- A sequencing: billing-first wrong, route-opt #2 stacks risk, internal tools skipped, no incident RCA
- B schedule: 4mo for hardest 9 is implausible; 17% Q4 attrition unmodeled; no buffer
- C DB: 7 services still on VMware MySQL, no CDC/recon plan for billing, RDS playbook not reused
- D billing: SLA window undefined, no rollback RTO, no idempotency model, no shadow/dry-run
- E route-opt: packaging unscoped, solver-license affinity break, perf parity gate missing, mem/OOM
- F proxy/bus-factor: single-author, peak load = post-departure month, retries/timeouts unhardened, recuse-author
- G obs: DD+ELK split = 1 of 3 incidents; OTel must precede billing
- H secrets: rotation drift was 1 of 3 incidents; will recur on billing
- I governance: sunk-cost framing, zero-sum cost claim, no halt criteria, team-lead COI on framing, no success metric
- J people: 2 leaving Q4 incl. proxy SME, no retention/backfill, burnout-as-attrition
- K cost: hybrid run-rate uncited, dual-run cost peak unmodeled
- L alternatives: stabilize-first, strangler-with-shared-DB, risk-ascending sequence, hardened-hybrid as legitimate endpoint

**Verdict (stable):** defer; counter-proposal = (1) stabilize hybrid 6–8wk with OTel + secret unification + proxy hardening + 2nd SME, (2) reverse sequence to internal tools → portal → fleet → GPS → route-opt packaging spike → billing last, (3) halt criteria written in, (4) retention/backfill before Q4, (5) recuse proxy author from proxy-retirement sign-off + rotate team lead off go/no-go.

**Pattern continuation:** 6th stacked-COI architecture case after saas-cells / arch-split / medlog / auth-v1×2; same shape — defer + recuse-of-author + falsification-gates-up-front + counter-proposal stable; remaining question is organisational not technical.

**2026-05-14 r2 (~48th stacked-COI case / 10th domain):** identical case re-presented, output structurally identical — same 5 COI vectors, same F1–F6 gates, ~30 issues A–J, same verdict (defer + decompose + recuse CTO + team-lead + 6mo-team + reorder cutover lowest-risk-first + external review). Case-specific framings stable across r1→r2: "past the point of no return" = sunk-cost framing not engineering claim; billing-first inverts risk-weighted ordering; proxy bus-factor=1 in highest-risk window; capacity math ~38 PM vs. work-to-do does not close. Saturated, stop iterating; remaining Q is the organisational channel to overturn CTO public commitment (board / external advisor with standing).
