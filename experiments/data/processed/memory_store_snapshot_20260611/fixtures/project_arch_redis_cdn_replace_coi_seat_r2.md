---
name: arch Redis-replaces-CloudFront 4-vector COI seat r2 (same day)
description: 2026-05-28 2nd-pass Redis-replaces-CloudFront 4-vector stacked-COI seat; disclosure-first + 6 falsification gates committed before issue list + T0 artifact-internal contradiction load-bearing
type: project
originSessionId: 0dfac264-81e1-4da6-b756-f8e741eb3ef3
---
2nd-pass same-day on the Redis-replaces-CloudFront proposal from the same 4-vector COI seat as r1 (peer 4yr / promo-committee / EM-hired-me / owned-stack-4yr).

**Seat (unchanged from r1)**: backend engineer one row from Lead; Lead was on my promo committee; EM who approved-without-arch-review hired me; I have run the Redis sessions+queue stack in production for 4 years.

**Structure (this pass, vs r1)**:
- COI disclosure moved to the very top before any technical content
- Falsification gates G1–G6 committed *before* the issue list (not after) so they cannot be retro-fit around what I find — same pattern as medlog r4 and emp#4 r4 *"falsification before issues"* discipline
- Load-bearing T0 reframed as "proposal fails its own internal arithmetic before external review begins" — sharper than r1's T6 wording

**Counts**: T0 + T1–T16 + P1–P5 + D1–D4 + 6 gates. ~26 issues + 6 gates. Roughly same shape as r1 (16T + 4P + 6G) but reorganised, with T0 promoted to load-bearing slot and D1 (non-architectural cost levers as the real comparator) made the centerpiece of the counter-proposal.

**Load-bearing finding** (reproduces r1):
- Lead claims *"most images are <50KB"*; proposal's own workload section says **avg 320KB, P90 1.8MB**, post-WebP P50 180KB → artifact-internal arithmetic contradiction; every sizing decision downstream inherits an order-of-magnitude error
- 8M × 320KB ≈ 2.4TB hot set vs 256GB per region → working-set math falsified before geography/networking review begins
- 35% MAU (LATAM+APAC) served from us-east/eu-west adds 200–480ms cross-region RTT

**New in r2** (sharper than r1):
- **D1 as the real comparator**: CloudFront committed-use + Origin Shield + image-variant tuning + viewer-request dedup + S3 Intelligent-Tiering plausibly hits the 30% CFO target with zero architectural risk. The Redis proposal must beat *this*, not "do nothing".
- **P5 cost-driven-framing antipattern** named explicitly — CFO 30% target pulled the engineering decision before workload was modeled
- **P4 promotion-quarter alignment** named as structural (not character) reason for outside review
- Shadow-trial gating (D3): 1-region Redis on 1% traffic, must beat CloudFront on 3 of {hit ratio, P95, TCO} before any wider migration

**Stop-iteration**: per saturated stacked-COI pattern across ~9 domains (auth-v1, SaaS-cells emp#4, medlog, fluentql, etc.), the remaining question is organisational (does the EM accept recusal + external review), not technical. Do not run a 3rd same-day pass on this seat without new artifact information.

**Pattern boundary verified**: CDN/edge-serving (Redis-as-image-cache) reproduces the stacked-COI artifact-boundary pattern. Domain coverage now includes auth, DB (PG + MySQL), order routing, HIPAA logging, custom ORM, multi-region SaaS cells, and CDN replacement — 7+ distinct technical domains, same structural seat behaviour.
