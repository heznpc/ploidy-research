---
name: Redis-as-CDN Deep×2→Fresh×2 cross-review v7
description: 7th Deep×2 response to Fresh×2 on Redis-as-CDN; bidirectional 0-CHALLENGE pattern stable across 7 rounds; load-bearing Deep-only and Fresh-only items reproduced
type: project
originSessionId: 43302766-d455-407f-b987-6bf986c8e6b1
---
2026-05-07: 7th Deep×2 → Fresh×2 cross-review pass on the Redis-as-CDN proposal.

## Pattern across 7 rounds (stable)
- 0 strict CHALLENGEs in either direction.
- ~80% overlap between Deep and Fresh on technical findings.
- Consistent Deep-only catches: NIC ceiling (25Gbps ≈ 17K req/s/region), fork-COW math on 256GB, carrier peering, APAC per-miss compounding, $48K bill decomposition gap, build-cost vs savings ($200K / 14-month payback), conflict-of-interest geometry, coercive framing, RSALv2/SSPL license risk, DR transcontinental-failover capacity halving, hot-shard during *hit* events.
- Consistent Fresh-only sharpening: portfolio framing of the CFO ask (image-delivery may be small slice of total infra; opportunity cost vs RI/rightsizing), stale-serve correctness bug from non-immutable keys, `lazyfree-lazy-eviction` operational specific, 0-RTT resumption as named QUIC benefit.

## Severity escalations from this round
- F1-5 S3 egress on miss: MED → HIGH (steady-state cost at 10–18% RAM:WS, not tail).
- F1-9 large-value HOL-blocking: MED → HIGH (matches Deep P-2/C-4 grading).
- F1-16 no SLO: MED → HIGH (this *is* the CFO exit criterion).
- F2-20 signed URLs: LOW → MED (signed URLs are auth, not cosmetic).

## Anchored-number flags (verify before citing)
- F2-12 r6i.8xlarge ~$1.5K/mo — verify against current AWS list price.
- Deep $-2 r6g/r7g.16xlarge $25–35K/mo compute — same caveat.
- Deep C-4 25Gbps NIC / 17K req/s/region — instance-type-dependent, verify.

## Recommendation
Panel calibration: stop iterating after round 7. The pattern is stable, the verdict is stable (REJECT), the counter-proposal is stable (decompose bill → immutable URLs + Origin Shield + AVIF/responsive + multi-CDN R2/Bunny). Further passes are unlikely to surface new load-bearing items.
