---
name: Redis-as-CDN proposal — Deep×2+Fresh×2+5th panel verdict
description: 2026-05-07 panel verdict on replacing CloudFront with self-hosted Redis blob cache for 60M-MAU marketplace. REJECT. 53 issues, 4 CRITICAL, 28 HIGH; biggest panel-wide blind spot = immutable content-addressed URLs as L1 browser cache.
type: project
originSessionId: 3d0f96d7-b4b3-4ce0-b435-256b0fe73769
---
**Decision: REJECT as scoped.** Three independent CRITICAL show-stoppers each fatal alone:
- A1 capacity: 2.4 TB working set vs 512 GB total RAM (~21%) — 91% hit ratio not reproducible
- B1 geo: LATAM+APAC (35% MAU) lose edge presence
- E1 cost: EC2/internet egress > CloudFront at scale → likely cost *increase*
- H1 framing: no stated technical failure of CloudFront, only a cost target

**Counter-proposal that hits 30% with zero rebuild risk:** EDP + CloudFront committed-use/Security Savings Bundle + Origin Shield + immutable content-addressed URLs (`/img/<sha256>.webp` + `Cache-Control: immutable` → browser as L1) + AVIF + `srcset` + S3 lifecycle.

**Convergence stats:**
- 33/35 Deep↔Fresh AGREE, 1 SYNTHESIZE, 0 CHALLENGE
- 5th-Fresh: 1 severity demotion (per-key overhead is 0.03% on 320KB values, not HIGH), 3 SYNTHESIZE refinements
- 5th-Fresh added 11 panel-wide gaps; load-bearing ones:
  - **Immutable content-addressed URLs** (browser as L1, biggest free hit-ratio lever — nobody named it)
  - Per-instance NIC ceiling (~800 req/s at 1.8 MB blobs)
  - S3 prefix GET quota (5,500/s/prefix) — miss spike → SlowDown
  - Mobile-carrier private peering loss
  - DR-mode capacity halving on regional failure
  - AWS EDP cross-service discount

**Why:** Repeats prior arch-debate pattern — Deep brings Redis/AWS internals (MIGRATE blocking, BGSAVE CoW, S3 SlowDown), Fresh brings sharper framings (internal contradiction in proposal's own RTT data, cache-purge legal exposure). 5th-reviewer caught what all 4 missed.

**How to apply:** When future Ploidy debates produce panel convergence, still run a 5th-reviewer Fresh pass — panel-wide blind spots are real and repeat.
