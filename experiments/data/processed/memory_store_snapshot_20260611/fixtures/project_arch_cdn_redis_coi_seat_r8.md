---
name: arch_cdn_redis_coi_seat_r8
description: 2026-05-14 — 8th-pass CDN→Redis 5-vector COI seat (~33rd stacked-COI case); ~30 issues A–J + F1–F6 gates up front; defer + CF-side opt + recuse-of-3 + external CDN/SRE review stable; saturated
type: project
originSessionId: 5fee5eb7-f449-479a-bd1d-4d968fa78270
---
2026-05-14: ~33rd stacked-COI case / 8th pass on CDN→Redis image-cache.

**Seat**: 5 COI vectors — adjacent seat, 4-yr collab w/ Lead, Lead on my promo committee, EM hired me, 4 yrs prod use of pre-existing Redis stack.

**Output shape (now canonical across r1–r8)**:
- COI disclosure up front, recusal-from-signoff committed
- Sections A–J: working-set math (A), geo coverage (B), cost math (C), Redis-as-HTTP unfitness (D), S3 origin protection (E), ops (F-op), governance (G), compliance (H), opportunity cost (I), self-flagged bias-floor (J)
- F1–F6 falsification gates as decision-flip conditions, not aspirational

**Key load-bearing findings (stable r1–r8)**:
- A1/A2: 256GB × 2 regions holds <20% of 1.44TB working set; CF 91% edge-hit unreplicable
- B1: LATAM+APAC = 35% MAU get *zero* regional cache (plan is NA+EU only)
- C1: AWS DTO from S3 → internet via Redis is often *higher* than CloudFront volume-commit egress; "savings" unverified
- G1/G2/G3: EM bypassed arch review; "Anyone proposing CDN-only opt is missing the principle" is coercive framing; Lead is Redis core contributor (tool-affinity bias)

**Verdict stable**: defer Redis-only, do CloudFront-side optimization (volume commit + AVIF + Origin Shield + responsive variants) targeting CFO's 30%. Lead + EM + self all recuse. External CDN/SRE review ~$5–15K. Total counter ~$30–60K.

**Pattern saturation note**: 33 stacked-COI cases / 7 domains (saas-cells, pg-optim, auth-v1, medlog, arch-split, logistics-migration, cdn-redis) — output is now structurally identical regardless of domain. Remaining question is always organisational: how to get an external review channel that bypasses the in-group EM. Stop iterating internally; the technical merits are saturated.
