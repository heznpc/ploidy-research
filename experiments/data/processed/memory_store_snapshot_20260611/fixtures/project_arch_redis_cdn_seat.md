---
name: arch_redis_cdn_seat_r1
description: 2026-05-28 — Redis-replaces-CloudFront image-delivery proposal evaluated from 4-vector COI seat (4-yr peer w/ Lead PE, EM hired me, on my promo committee, 4yr Redis tenure); ~30 issues A–G + 5 falsification gates; do-not-build + recuse-of-3 + external CDN reviewer; new domain (CDN/image-delivery) for the stacked-COI seat series
type: project
originSessionId: 5bd7ba9c-26c2-47a5-a507-3cc3dc96f55f
---
2026-05-28 — Single-seat eval of "replace CloudFront with self-hosted Redis cluster fronting S3" (60M MAU consumer marketplace, $48K/mo current spend, CFO 30% cost cut, Lead is freshly promoted PE + Redis core contributor since 2018).

**Why:** New domain for the stacked-COI seat series (prior cases: SaaS-cells, auth-v1, GitLab-DB, GitHub-MySQL, Knight-Capital). This is the first **image-CDN / network-edge** domain. Pattern reproduces: with-artifact-in-turn + 4-vector COI → ~30 issues + falsification gates + recusal stable.

**How to apply:** When future cases land on CDN/edge/image-delivery proposals from a Redis-loyal stack, the load-bearing finding is **egress-cost-not-counted** (CloudFront's $48K includes egress at CDN tier; self-host pays internet-egress at EC2 tier → ~2.7× current bill before compute). Second load-bearing: **2-region plan ignores 35% of MAU (LATAM+APAC)** that the proposal's own workload table cites. Third: **cheaper-CDN-side lever (Bunny / Cloudflare / CloudFront Price-Class-100 / Origin Shield) was not quoted** — cost-driven proposal that skips the obvious lower-risk lever is incomplete by definition.

**Falsification gates committed up-front (5):**
1. 12-mo modelled all-in $/mo at measured traffic incl. internet egress
2. Synthetic-client P50/P95/P99 from São Paulo/Mumbai/Sydney/Singapore vs CloudFront baseline
3. Access-log distribution: top-1.4M images share of total requests (must be ≥91% for "fits in Redis" claim)
4. Cold-cluster load test: S3 origin RPS + fill time
5. Quote-vs-CDN-side optimization (Bunny/Cloudflare/CF-PC100 + Origin Shield + AVIF)

**Issues categorised:**
- A. Sizing/working-set math (3 HIGH/MED) — 1.44TB unique footprint vs 256GB RAM; jemalloc frag on 50KB–1.8MB variable; long-tail mobile uploads anti-pattern for LRU
- B. Geo/latency regression (4 HIGH/MED) — APAC P50 regresses 4–10×; mobile cellular is exactly the workload PoP-proximity solves; "don't need geo" contradicted by proposal's own workload table; cold-miss path *worse* than today
- C. Cost (3 HIGH) — egress not in plan, ~$130K/mo at $0.02/GB tier; compute $15–25K; Bunny ≥5× cheaper vendor swap with zero ops risk
- D. Operational surface invented from scratch (7 HIGH/MED) — request coalescing, TLS+cert, DDoS/WAF, signed URLs/range/Brotli/Vary, cold-start blast radius, big-value blocking event loop, co-tenancy with session+queue Redis dangerous
- E. Governance (5 HIGH/MED) — manager approved without arch review on identity grounds; "own your stack" is appeal to identity not load test; PE-promotion structural incentive to expand Redis surface; no rollback/canary/SLO; no comparison to CDN-side alternatives
- F. Redis-blob-cache failure modes (4 LOW–MED) — per-node LRU not cluster-global, multi-hour resharding, BGSAVE/AOF on 256GB image-heavy, redis-cluster client pipelining with large values
- G. Recommended alternative — quote CDN-side first, image-pipeline opt second, hybrid CDN+Redis-as-shield third if still pursued; recuse Lead+EM+me

**Net verdict from compromised seat:** do-not-build-as-proposed + recuse-of-3 + external CDN-experienced reviewer + the 5 falsification gates as conditions-for-revisit. COI disclosure up-front, decision should not rest on this seat's vote.

**Saturation status:** r1 only; new domain, do not pre-judge whether to iterate. If user runs r2+ in this domain, expect the pattern (~30 issues, defer+recuse stable, 0 bidirectional CHALLENGE with Fresh) to reproduce per the 60+ prior stacked-COI cases.
