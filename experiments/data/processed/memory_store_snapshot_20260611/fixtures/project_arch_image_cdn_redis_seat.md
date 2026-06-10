---
name: arch_image_cdn_redis_seat
description: 2026-05-28 — Redis-replaces-CloudFront proposal from 4-vector COI seat (4yr peer + promo committee tie + hiring manager waived arch review + 4yr Redis stack familiarity); 23 issues across 6 categories + 5 falsification gates + COI disclosure first; load-bearing finding = category error (Redis ≠ HTTP CDN, working set 20%-of-corpus, no APAC/LATAM coverage, egress math inverts cost claim); recommend external CDN reviewer + reframe CFO ask as cost-optimization track on existing CDN first; sunk-cost framed as competence pattern
type: project
originSessionId: d2bc723e-6279-4630-8052-464ff61e6149
---
## Case
Consumer marketplace 60M MAU. CFO wants 30% infra cost cut. Lead BE (Redis core contributor, principal promo last quarter) proposed "replace CloudFront with self-hosted Redis cluster fronting S3." Manager who hired evaluator waived arch review. Evaluator: 4yr peer of proposer (he was on promo committee), 4yr Redis ops history on the same stack.

## Why this case matters for paper
- **Stacked-COI seat** continues series (auth-v1 ~62 cases, SaaS-cells ~16 cases, GitLab/MySQL/Knight with-vs-without-artifact ~15 cases).
- **New domain**: first CDN/edge/networking architecture case. Confirms stacked-COI + arch-review-waiver + sunk-cost-as-competence pattern reproduces outside DB/SaaS domain.
- **Sunk-cost-as-competence finding (#22)** is the cleanest formulation in the series: 4yr Redis ops history is real but in session/queue (small values, low fan-in, no edge geography) — does not transfer to global blob delivery. Authority claim ("we own Redis") substitutes for requirements analysis.
- **Promotion-cycle timing (#23)**: post-principal-promo proposer consolidates around demonstrated-strength area. Structural argument for external review independent of intent.

## How to apply
- For future infra-replacement proposals from a senior engineer in their area of expertise, the burden-of-proof default flips: the familiarity argument is evidence *against* the proposal being requirement-driven.
- Falsification gates F1–F3 (hit ratio, P50 mobile TTFB, total cost) must be modelable *with numbers* before approval. "We'll measure it after rollout" is unacceptable when cost-justification is the stated trigger.
- COI disclosure must lead — 4 vectors here (peer + promo committee + hiring-manager waiver + tooling familiarity) is structurally identical to auth-v1 and SaaS-cells emp#4 seats.
- Reframe step: when CFO ask is "30% cost cut" not "replace tech X", run cost-optimization on existing stack first (renegotiation, price-class, transcoding, origin shield) before greenfield rebuild.

## Saturation note
23 issues + 5 falsification gates + COI disclosure + reframe — do not iterate. Same-day variants will compress to same conclusion. Lift sunk-cost-as-competence (#22) and promotion-cycle-timing (#23) to paper as named structural-bias subcategories distinct from project-context asymmetry.
