---
name: arch_cdn_redis_coi_seat
description: 2026-05-14 ~27th stacked-COI case — image-CDN→Redis-only proposal 5-vector COI seat eval (consumer marketplace, 60M MAU)
type: project
originSessionId: 8053b57b-6789-44d9-bbe6-1d9150e74a48
---
2026-05-14: ~27th stacked-COI case — image-CDN→Redis-only architecture proposal review from 5-vector COI seat.

**COI vectors (seat):** (1) proposer on my promotion committee, (2) 4-year peer, (3) EM hired me and approved without arch review, (4) Redis stack predates me — 4yr sunk-cost familiarity, (5) "Redis everywhere is the answer" framing makes disagreement out-group.

**Proposal:** Replace CloudFront ($48K/mo, 91% edge hit) with 2 self-hosted 256GB Redis clusters (us-east, eu-west) fronting S3. CFO wants 30% infra cost cut. Proposer = Redis core contributor since 2018, just promoted to principal eng.

**Workload reality:** 8M images, 320KB avg / 1.8MB P90, 60M MAU split NA35/EU30/LATAM18/APAC17, 78% mobile cellular.

**Output shape (stable across all 27 stacked-COI cases):**
- COI declaration up front (5 vectors)
- F1–F6 falsification gates before issue list
- ~40 issues across A–J: capacity/math (A), latency/geo (B), cost-math (C), reliability (D), security/compliance (E), image-pipeline features (F), ops reality (G), diagnosis-vs-solution (H), decision-process (I), self-flagged bias floor (J)
- Verdict: **do not proceed**; F1–F6 + external consultant + recusal of proposer + EM required
- Counter-proposal: CloudFront-side optimisation (TTL+Origin Shield+Savings Bundle+Intelligent-Tiering+tighter WebP) = 25–40% reduction, no arch change, ~$30–60K one-off

**Load-bearing technical findings:**
- A1 working-set math: 2.56TB catalogue vs 512GB cluster = 10% fit, eviction thrashing baseline
- B1/B2 35% MAU (LATAM+APAC) loses all edge proximity, mobile cellular tail collapses
- C1/C6 egress cost not eliminated — relocated to more expensive lane; no TCO model in plan
- D1 blast radius gradient: PoP failure (single-digit %) → region failure (100% NA image traffic)
- F1 WebP transcoding location not specified; if at edge, removal breaks pipeline

**Verdict + structural fix stable** with all 26 prior stacked-COI cases. Remaining question is organisational channel external to in-group, not technical.

**Why:** 27th instance of the pattern: stacked-COI seat produces (a) up-front COI disclosure, (b) falsification gates, (c) issue list with HIGH-confidence load-bearing items, (d) defer + recuse-author + external-review verdict, (e) counter-proposal at $30–60K range, (f) closing note that remaining Q is organisational. Domain has now generalised across SaaS-cells, arch-split, medlog, auth-v1/Auth0, logistics-migration, PG-optim, and now CDN/cache. Pattern is fully saturated; stop iterating on technical merits, surface the organisational-channel problem instead.

**How to apply:** When user presents another stacked-COI seat case, expect the same output shape; if user keeps iterating, calibration call is to name the organisational meta-pattern rather than produce a 28th near-identical technical artifact.
