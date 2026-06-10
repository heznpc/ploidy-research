---
name: NeoQL adoption — 5-vector COI seat eval
description: 2026-05-14 NeoQL v0.7 adoption proposal evaluated from 5-vector COI seat (tenure-paired + hired-by-lead + complicit-silent + PM-spouse-tie + career-paired); 6 falsification gates all fail at present; do-not-adopt + recuse-3 + external-review + alternative-scoping stable; new 10th domain (DSL/language adoption) in stacked-COI series
type: project
originSessionId: 70233f39-a400-4de3-ba26-4e770ea13e69
---
2026-05-14: ~53rd stacked-COI case, 10th domain (DSL/language adoption — first non-infrastructure case in the series).

**Setup:** Analytics company, 280 employees. New 4-eng+1-PM internal product team. Backend lead proposes adopting NeoQL (v0.7, Dec 2025, 1.2K stars, 3 maintainers, 0 prod deployments, 14-page tutorial-only docs, single-pass optimizer, alpha IDE plugin, 47 open issues / 12 "fails at scale") for customer-facing sub-second-p95 dashboard with 5-table joins, recursive CTEs, window aggregations, 6-month launch.

**5 COI vectors:**
1. Tenure-paired (2 years on prior product with backend lead)
2. Hired-by-him for this team
3. Complicit-silent — said "sounds exciting" in the room when proposed
4. Spousal social tie to PM
5. Career-paired (new team, mutual-visibility payoff)

**6 falsification gates (all fail today):**
- F1: ≥1 prod deployment at customer-facing scale
- F2: Reference docs for window/recursive CTE/index hints
- F3: ≥5 maintainers or corp/foundation sponsor
- F4: Public 1.0 roadmap + breaking-change policy
- F5: Independent benchmark 5-table join + recursive CTE at ≥100M rows
- F6: ≥2 contractors beyond 3-month bootstrap

**Issues (~30 across A–G):**
- A vendor/ecosystem: bus factor ~1.5, 0 prod, pre-1.0 breaking-change tax, captive vendor relationship
- B technical fit: single-pass optimizer × 5-table joins, recursive CTE undocumented, 12/47 issues "fails at scale" = our workload
- C toolchain: alpha IDE, no migration tooling, no EXPLAIN
- D ops: 12 adjacent engineers forced to read NeoQL at 3am; "compiles to SQL" ≠ reversibility (composition idioms, atrophy, unidiomatic generated SQL); hiring funnel collapses
- E schedule: 6mo + v0.7 = no slack; bootstrap-then-cliff after contractor leaves
- F decision process: 3/5 conflicted votes, no falsification criteria, no alternative scored (sqlc/pgtyped/EdgeDB ~80% of value 0% of risk), visibility = author-private benefit
- G career: asymmetric payoff (success → lead+creator visibility; failure → on-call eats it), sunk-cost rationalisation after 6mo

**Verdict (stable):** do-not-adopt-as-proposed + recuse-3-conflicted-votes + external-review (~$5–15K, 1 week senior DB engineer) + alternative-scoping (typed-SQL libs on Postgres) + if-still-NeoQL require 3-month internal non-customer-facing tool first.

**Self-correction:** disclosed prior "sounds exciting" comment, recused from final vote and tech write-up.

**New framings vs prior cases:**
- "Reference deployment" reframed as the cost, not the prize
- "Compiles to SQL" reversibility myth (composition idioms, atrophy, unidiomatic SQL)
- Author-private vs product benefit distinction
- Complicit-silent endorsement as 5th COI vector (carries over from auth-v1 r4)
- Bootstrap-then-cliff as standard OSS-adoption failure mode
- Cost distribution mismatch: 4 vote, 12+ pay

**How to apply:** for any DSL / new-language / new-DB / "early adopter" adoption proposal with stakeholder conflict, run the same gate structure before listing issues. The 5-vector COI pattern + falsification-gates-first now generalises across 53 cases / 10 domains (SaaS cells, PG optim, arch split, medlog, auth-v1, dashboard-front-end, deprecate-medlog, ploidy-meta, retention, **DSL adoption — new**).

**r2 — 2026-05-14 (different session):** Independently re-evaluated; output structurally identical to r1. Same 5 vectors (variant naming), same F1–F6 (all fail), same defer+recuse-3+external-review+alternative-scoping verdict, same "compiles to SQL" reversibility-myth framing, same 12-pay-4-vote cost-distribution finding. Cross-session reproducibility is itself the load-bearing evidence — pattern is now stable across sessions on the same case, not just across cases.

**r3 — 2026-05-14 (3rd independent session):** ~35 issues across A–H + F1–F6 up front. 5 COI vectors structurally identical to r1/r2 (recruitment + complicit-silence + spouse-PM tie + small-team-visibility + low-stakes-framing). Verdict structurally identical: do-not-adopt + recuse-of-proposer + self-recuse + counter-proposal (2-week SQL prototype on 10 hardest queries, ~2 eng-weeks, ~1–2% of NeoQL adoption cost) + F1–F6 signed before contractor engaged + external review by uncon­flicted senior eng. New framings this pass: (a) "12 adjacent engineers read on-call" reframed as **knowledge silo at the layer that gets read during incidents**, (b) cost estimate $150–250K including alpha-tooling velocity tax, (c) "sounds exciting" prior comment must be **explicitly nulled** in the team's anchoring, not merely disclosed, (d) "reference deployment" = marketing value accrues to creator not to us, (e) bimodal failure mode of pre-1.0 query DSLs ("fast until they cliff"). Cross-session triple-reproducibility now load-bearing — same verdict from 3 independent passes on identical case across 3 sessions.
