---
name: 3-region cell architecture final verdict
description: 2026-05-08 Deep×2+Fresh×2 verdict on Series-A 3-region/24-cell/CRDB/Istio/custom-GLB proposal — REJECT, recuse authors, staged counter-proposal
type: project
originSessionId: e10062ad-9707-4bc9-be33-aceb57db7371
---
2026-05-08: 3-region cell architecture proposal final verdict (Series-A, 200K users, 850 RPS, 12 engineers, $94K → $1.4M+ infra).

**Decision: REJECT as packaged. Recuse CEO + lead architect + employee #4. Re-vote on staged counter-proposal with CFO/board capital-allocation sign-off.**

**Convergence: Deep×2 + Fresh×2 + bidirectional cross-review — 0 strict CHALLENGEs.**

**~70 confirmed issues:**
- 6 CRITICAL (escalated from HIGH): P8 no-SLOs, R2 3-undeclared-COIs, $5 Series-A-runway, T2 product-velocity-to-zero, D4 no-migration-plan, R9 no-CFO-signoff
- ~50 HIGH across premise/capacity/DB/mesh/GLB/cells/team/cost/risks/governance/missing
- 4 MEDIUM: CRDB license, vendor lock-in, two-tier eng org, chaos-NIH
- 1 LOW: us-east-1 history → passive DR is defensible 5%

**Load-bearing chain:** P5 (wrong question) + P6 (wrong evidence — neither incident solved by proposal) + R1 (weekend-retreat 2-author origin) + R2 (3 COIs) + R6 (bundled all-or-nothing) + $5 (no capital authority) + T1 (5 unhired FTEs) + D8 (PG at <1% — no problem to solve).

**Fresh-only adds Deep missed:**
- True Y1 cost likely $4–5M not $3.2M (egress unbroken-out)
- us-east-1 outage history → passive DR is the defensible 5%
- "Punching above our weight" as cultural defect, not strategy
- **Lead-architect COI > employee-#4 COI** (weight differentiation)
- Founder-departure soft-power if rejected
- CRDB managed-vs-self-hosted ambiguity
- Recusal assumes a vote body — may not exist
- Enterprise SLA / data-residency contracts unaudited
- Customer churn during 12–24mo migration
- No named DRI per system
- No "what happens if we don't" section

**Deep-only Fresh missed (15 items):** R5 reversibility, R7 falsification, R8 off-ramp, C5 "8 cells aesthetic", D3 data-locality, D6 0/12 CRDB experience, D7 DR runbook rewrite, S2/S3/S4 mesh specifics, G3 health-aware = research-grade, G4 unfalsifiable LB spec, L2 tenant-to-cell mapping, T6 two-tier-org, $1 gross-margin destruction, M3 per-tenant isolation, M6 observability prereq.

**Counter-proposal (stable):** SLOs → observability → Aurora → eu read-replica + CloudFront → deploy safety + circuit breakers → per-tenant rate-limits → defer cell/multi-region/CRDB/Istio/GLB until ≥5K RPS sustained AND eu/apac > 25% AND written capacity model. Re-vote with authors recused, CFO/board signoff, named DRIs, arch-decision body established.

**Why:** 3rd recurrence of B2B-SaaS-adopts-big-tech-architecture pattern (prior: `arch_eval_saas_cells.md`, `project_arch_split_*`). Structural failure mode: peer-company name-checks substitute for capacity models; authorship attachment + career upside drive evaluator capture; bundled all-or-nothing proposals prevent staged de-risking.

**How to apply:** When user presents an architecture proposal with (a) peer-company analogies, (b) bundled scope, (c) author = decider, (d) >5× current scale targeted, (e) no capacity model — flag the recurrence pattern up front. The counter-proposal shape (SLOs first → observability → managed-DB-HA → measured triggers) is reusable across this entire pattern class.
