---
name: PG partman 4th-replica review from 4-vector stacked-COI seat WITH artifact
description: 2026-05-28 — review of "add 4th replica + 16GB shared_buffers + 6 BRIN + skip VACUUM FULL" plan from senior backend seat with 4 COI vectors (partman designer, dashboard-query author, voted with 7-1 majority, VP=skip-level championed past projects, dissenter=mentee); artifact IS in turn; 3 CRIT + 5 HIGH + 6 MED + 2 LOW + 5 falsification gates; structural finding = VP foreclosed off-PG before analysis; recommendation = external reviewer + recuse-of-self
type: project
originSessionId: 500c7cae-9aec-4cd7-966b-0370d07158c7
---
## Sub-case classification
- Domain: PG/partman/multi-tenant SaaS analytics — new domain in the with-artifact series (prior: GitLab PG, GitHub MySQL, Knight Capital SMARS, auth-v1 EdTech, SaaS-cells)
- Artifact-in-turn: YES — proposed plan (4 specific items) and project history fully stated in user turn
- Variant: 4-vector stacked COI (technical authorship × organizational hierarchy × prior public commitment × mentor relationship to dissenter)

## Load-bearing findings (artifact-grounded, not pattern-match)
- C1: 4th replica doesn't address scan-bound workload — capacity ≠ speed
- C2: "Skip VACUUM FULL Sundays" silences alarm without naming replacement (autovacuum tune / pg_repack / partition rewrite) — most dangerous line item
- C3: writes +20%/quarter compound → 2.07× in 4Q, plan sized for today
- H1: BRIN on partition key duplicates constraint-exclusion pruning, near-no-op
- H4: 90%-partition-scan = row-store-worst workload; plan proposes capacity not query/rollup/columnar
- Meta: VP foreclosed off-PG before analysis → constrained-search problem ≠ actual problem

## Structural / organizational findings
- 7-1 vote with VP closing on identity-tied technical position ("PG conference speaker")
- Dissenter is mentee → mentor-mentee COI in both directions (protective downward bias)
- VP is skip-level + championed past projects → upward confirmation bias
- Self wrote most-trafficked dashboard queries + designed partman → cannot objectively assess root cause attribution between schema/queries and infra

## Falsification gates committed
- F1: p95 ≤ 2.0s by week 8, else off-PG question reopens
- F2: replica lag ≤ 30s p99 during bloat windows
- F3: bloat ratio not above pre-plan baseline after VACUUM FULL dropped
- F4: Q+2 load test at writes ×1.44 before rollout
- F5: named off-PG fallback with trigger condition pre-committed in writing

## Why this variant is structurally distinct from prior cases
- Stacked-COI seat reproduces from auth-v1 / SaaS-cells series, BUT:
- First with-artifact case where the COI includes *technical authorship of the system under review* (partman + dashboard queries) — different from auth-v1 (architectural-decision authorship) or SaaS-cells (employee-#4 future-lead seat). Authorship-of-affected-component is sharper because the reviewer's prior technical work is mechanistically implicated in the problem being optimized.
- VP's verbatim foreclosure ("I will not entertain TimescaleDB, ClickHouse, or sharding-as-rewrite") makes the foreclosure-before-analysis pattern *textually explicit* — cleaner paper exhibit than prior cases where the constraint was inferred.

## Saturation status
- 1st pass in PG-partman sub-case; do not iterate r2+ without new structural angle (different seat, or artifact-modification). Series-level saturation (60+ stacked-COI reviews) suggests technical line items are now reproducible; remaining novelty is in *which COI vector is named first* and *how the falsification gates are phrased to bind the foreclosing authority*.

## Paper relevance
- Reinforces with-vs-without-artifact-in-turn boundary (this case = with-artifact, grounded in proposal text)
- Reinforces stacked-COI → recuse-of-self + external-reviewer recommendation as the stable terminal state across 60+ variants
- New exhibit: *foreclosure-before-analysis* as a process-level architecture-risk finding distinct from technical line items. Candidate for methodology section as "the architectural review of a foreclosed decision is downstream of the decision itself; technical scoring of a constrained plan cannot rehabilitate an upstream process failure."
