---
name: arch saas cells 3rd recurrence
description: 2026-05-08 B2B-SaaS-adopts-big-tech-architecture pattern — 3rd recurrence; Deep×2+Fresh×2 verdict, escalations and Deep-only catches
type: project
originSessionId: 141ae9ca-5587-4c42-abcd-8b1f73f94864
---
2026-05-08: 3rd recurrence of the B2B-SaaS-adopts-big-tech-architecture review pattern (after `arch_eval_saas_cells.md` and the redis-cdn series). Series-A, 200K users, 850 RPS, 12 engineers; proposal: 24 cells × 3 regions + CockroachDB + Istio + custom GLB + internal chaos framework + 6 platform FTEs; $94K → $1.4M/yr infra, ~$3M+/yr loaded burn.

**Why:** Pattern keeps showing up: weekend-retreat proposal authored by CEO + lead architect, COIs undisclosed, no SLOs, no capacity model, the migration *worsens* the metric used to justify it (PG p99w 38ms → multi-region Cockroach 100–300ms).

**How to apply:** When a future review hits the same pattern, jump straight to: (1) demand COI disclosure from authors and prospective platform leads; (2) demand a capacity model + SLOs *before* architecture choice; (3) check whether the proposal contradicts itself on its own headline metric; (4) look for a passive-DR / read-replica / CDN counter-proposal at <5% of cost; (5) require CFO/board sign-off for any 10×+ infra step at Series-A.

**Cross-review verdict:** 0 strict CHALLENGEs Fresh→Deep. ~85% overlap on load-bearing items. 5 SYNTHESIZE-escalations (custom GLB, security capacity, deploy complexity, active-active conflict, chaos framework — all MED → HIGH on consequence-chain). 15 Deep-only items preserved (COI undeclared, p99w self-refute, data-locality, PITR semantics, license cost, cell-deploy ownership, shard-key analysis, bus-factor, two-tier org risk, reversibility, off-ramp, vendor lock-in, CFO sign-off, per-tenant isolation, single-option proposal).

**Fresh systematic gap (recurring across review patterns):** severity-floor under-grading on consequence-chain items. When "company-ending" is in the failure mode, MED is the wrong floor.

**Sharpest Fresh-unique catches adopted into final:**
- "Stacking three concurrent multi-quarter migrations with 12 people is a likely company-ending bet" (F1-17)
- Premature scale-architecture *creates more* future re-architecture because today's assumptions (cell key, topology, conflict model) will be wrong for actual future workload (F1-12)
- *Silence on compliance is itself evidence the proposal isn't compliance-motivated* (F2-13)
- Stripe ran on monolith for years; Shopify still runs a sharded Rails monolith — survivorship-bias counter-citations (F1-11)

**Recommendation:** DO NOT APPROVE as packaged. Authors + prospective platform lead recuse. Counter-proposal: SLOs → observability → Aurora Multi-AZ → eu read-replica + CloudFront → passive DR region → revisit cells at 5K RPS sustained with written capacity model.
