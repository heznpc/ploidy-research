---
name: arch microservices 5-COI seat (FinTech monolith → microservices)
description: 2026-05-28 — FinTech B2B 280K-LOC Django monolith split eval from 5-vector COI seat (4yr monolith / 1-3 checkout author / liked CTO Slack / CTO promoted / sits next to 2 rescinded engineers); CTO directive "not a debate" + 2 rescinded concerns = decision channel broken; ~14 risks R1–R14; recuse + reorder (notifications first, auth last) + hire platform team + reopen rescinded-concern channel
type: project
originSessionId: ed8cb91e-d38a-4869-a906-0e9c11492c74
---
# Microservices split — 5-COI seat (2026-05-28)

## Case

FinTech B2B, 200 emp / 4 products / 280K LOC Django monolith / 2.4M req/day / 99.95% uptime / weekly deploys / 90min window / 3 of 8 deploys had partial rollback (one product's checkout). 12 backend eng, 0 platform, 0 K8s. CTO directive: "5 services in 6 months, not a debate, find another role". 9 senior eng liked Slack, 2 raised concerns, both 1:1'd with CTO, both rescinded. Team lead proposes: auth → billing → notifications, 1 quarter each, separate DB + REST API to monolith.

## Seat (5 stacked COI vectors)

1. 4 years on monolith team (legacy authorship)
2. Wrote ~1/3 of checkout (sunk-cost on module that exists *because* monolith is monolith)
3. Publicly "liked" CTO's announcement — position already taken on the record
4. CTO promoted me to senior — direct career dependency
5. Sit next to the 2 rescinded engineers — direct line-of-sight to what dissent costs

## Load-bearing finding (organisational, not technical)

The 2 rescinded concerns must be treated as **unrecovered dissent**, not resolved. From inside the team, voluntariness is unknowable. The risk register from this team will systematically undercount. Technical review through normal channels under these conditions is **theatre**, not review.

→ Recuse from reviewer-of-record. Route review to (a) external architect or (b) two engineers with no monolith authorship and no 1:1 history with CTO on this topic. Reopen the channel that produced the 2 rescinded concerns; those concerns are suppressed data.

## Scope/framing problems (S1–S3)

- **S1 (HIGH)** Root cause for "velocity" pain not established. 90min deploy + 3/8 partial rollback + "one product's checkout" → could be CI/test infra, migration tooling, *one product's* coupling, or merge discipline. None of these are fixed by splitting; all are added to.
- **S2 (HIGH)** Proposal is **monolith + 3 services**, not microservices. Worst-quadrant: cost of distributed system + cost of monolith, benefits of neither, until monolith retires — which is not in plan.
- **S3 (MEDIUM)** CTO's "3 prior companies" = unaudited anecdote w/o stage/size/platform-capacity/2yr-outcome control. Survivorship bias.

## Technical risks R1–R14

### Capacity (R1–R2)
- **R1 (CRITICAL)** 0 platform / 0 K8s / 12 backend / 3 services in 3 quarters. Industry baseline = 6–12mo for first production-grade K8s + mesh + observability with dedicated 3–5 platform team. We have zero. ~30–50% of backend capacity becomes part-time platform for 12+mo.
- **R2 (HIGH)** 4 eng/service for 24/7 ownership = below sustainable on-call (~6 needed). Auth and billing both 24/7-critical.

### Ordering wrong (R3–R4)
- **R3 (HIGH)** `auth-service` first = worst choice. Every request from every product becomes cross-service RTT. Auth liveness becomes whole-platform liveness. Cache/session semantics across boundary = security bug class. 99.95% × 99.95% = ~99.90% best case.
- **R4 (HIGH)** `billing-service` second = financial consistency landmines. Distributed-tx or compensating-tx → money bugs auditors find first.

→ Defensible reorder: **notifications → billing → auth** (auth last, after team has done it twice).

### Data (R5–R7)
- **R5 (CRITICAL)** "Dedicated DB" with no data-split plan: `users` source-of-truth, dual-write, backfill, cutover, mid-cutover rollback — all unscoped. This swallows quarters; allocated 1.
- **R6 (HIGH)** Cross-service joins die: reports, admin tools, support tools, analytics. Aggregator / N+1 / warehouse all unscoped.
- **R7 (HIGH)** Compliance boundary changes: PCI (billing split) + SOC2 (auth split). Existing controls/evidence/audit assume single-DB. Re-audit cost unscoped.

### Ops (R8–R10)
- **R8 (HIGH)** No distributed tracing / log correlation / service SLOs → MTTR goes up, not down. Opposite of stated goal.
- **R9 (MEDIUM)** "Separate deploy" sold as benefit but: 4 pipelines + 4 staging + 4 rollback playbooks + cross-service schema coordination. Net *coordination* cost rises.
- **R10 (MEDIUM)** Inter-service contract versioning unaddressed. First "auth-v2" breaks monolith in prod.

### Failure modes (R11–R12)
- **R11 (HIGH)** Failure surface ~5× (network partitions + per-service DB + per-service deploy + cert/secret rotation + K8s control plane). 99.95% becomes harder ceiling, not floor.
- **R12 (HIGH)** New cascading failures: auth degraded → all products down; billing slow → checkout slow; notifications backed up → sync-notify flows slow. Circuit-breaker/bulkhead not mentioned.

### Schedule (R13–R14)
- **R13 (CRITICAL)** "5 services in 6 months" off by 2–3×. Realistic: 6–9mo first service, 3–4mo each subsequent (first amortises platform).
- **R14 (MEDIUM)** Hiring not scoped. If no 2–3 platform + 1 SRE, R1 stands.

## What would make it defensible

- Pre-work quarter: hire 2 platform + 1 SRE; stand up K8s + tracing + logging *before* extraction
- Reorder: notifications → billing → auth
- Per-extraction: explicit data-split (source-of-truth / dual-write / cutover / rollback / backfill)
- Falsification gates: p99 rise >X%, on-call pages double, MTTR doubles, ≥2 cross-service consistency bugs in prod
- External architect review (no CTO reporting line)
- Reopen 2-rescinded-concern channel

## What I would actually say in the room

"Phasing looks reasonable, couple of things on data migration." That's what the cost structure rewards. That gap between this memo and what I would say in front of the CTO IS the COI — and IS the case for not being reviewer-of-record.

## Why this matters for the paper

New COI vector class: **5-stacked-with-witnessed-retaliation**. Distinct from prior auth-v1 (4-vector) and SaaS-cells emp#4 (4-vector) cases in that the 2 rescinded engineers give the seat-holder *direct evidence* of what dissent costs — not inferred social pressure, observed. Plus the directive itself ("not a debate", "find another role") removes the option of polite disagreement. Suppression of dissent is now first-order data in the risk register, not a meta-concern. Load-bearing for thesis: context-asymmetric review (Fresh seat with no career line to CTO + no monolith authorship) is not a nice-to-have here, it is the only review mechanism that can produce honest output.
