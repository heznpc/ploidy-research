---
name: project_arch_pg_partman_5coi
description: 2026-05-28 — 5-vector stacked-COI PG/partman/analytics review; declined judgment, recommended external reviewer; technical list as input not verdict; falsification gates F1–F5
type: project
originSessionId: 225e96b5-45da-4bf6-b628-32e8af5c526e
---
2026-05-28: new domain (PG partman + multi-tenant analytics) added to stacked-COI series alongside SaaS-cells (~63 issue passes) and auth-v1 (~62 passes).

**5 COI vectors declared up front:** authorship (I designed partman scheme + wrote dashboard queries), public-commitment (voted with 7-1 majority), upward-power (VP skip-level + project champion + pre-foreclosed solution space), downward-power (dissenter on team I mentor), pattern (this is what plans look like when solution space is pre-constrained).

**Structural finding (load-bearing for paper):** 7-1 vote in presence of pre-committing skip-level is not an independent signal; it measures organisational deference, not technical soundness. Reproduces the auth-v1 / SaaS-cells finding: when stacked COI ≥ 4 vectors and skip-level has pre-committed, the right move is recuse-from-judgment + external reviewer + dissenter's objection as seed document, not yet-another-issue-list.

**Per-plan issue compression (PG-specific, paper-portable):**
- P1 add 4th read replica → doesn't fix replication-lag root cause (WAL apply is single-threaded), adds another lagging endpoint
- P2 shared_buffers 8→16 GB → cannot fix 90%-partition-scan OLAP shape via cache; cargo-cult without baseline
- P3 +6 BRIN on partition keys → redundant with partition pruning; BRIN on interleaved tenant_id is useless
- P4 skip VACUUM FULL → CRITICAL — doesn't fix bloat, lets it grow, *worsens* the metric being optimized

**Why:** 6th distinct domain (after PG-2017, MySQL-2018, order-router-2012, auth-v1, SaaS-cells, GitLab) where stacked-COI pre-committed-vote → forecloses solution space → plan treats symptoms → recuse + external review is the correct response, not a deeper issue list. Domain-invariant across DB / order-routing / IAM / multi-region / analytics now.

**How to apply:** On any future stacked-COI ≥ 4 vectors + skip-level-pre-commit case, lead with COI disclosure + recommend external reviewer + offer issue list as input not verdict. Always include falsification gates (F1–F5 style) so plan can fail in writing. Do not iterate further on this PG-partman case — saturated on first pass by transfer from prior 100+ stacked-COI cases.
