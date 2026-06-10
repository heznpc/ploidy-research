---
name: Redis-as-CDN — Deep×2 response v5 to Fresh×2
description: 2026-05-07 5th round Deep×2→Fresh×2 cross-review on Redis-as-CDN; Fresh~80% overlap with Deep; systematic Fresh gap = severity-floor under-grading on consequence-chain items (HTTP semantics, signed URLs, persistence, resharding, CoI all graded MEDIUM/LOW when load-bearing); 13 Deep-only items reproduced (NIC ceiling, hot-shard, fork-COW, MIGRATE, carrier peering, hit-ratio fallacy, HTTP/3, miss-chain, compute $, CFO arithmetic, 8M anchor, transcode location, promotion-optics-as-mechanism); verdict REJECT stable across 5 rounds
type: project
originSessionId: 4d890340-d894-4466-915c-451863dfd2fd
---
5th-round Deep×2→Fresh×2 cross-review on Redis-as-CDN proposal.

**Coverage:** Fresh×2 produced ~16–18 points each; ~80% overlap with Deep×2 on substance. Verdict REJECT held.

**Fresh systematic gap (recurring):** severity-floor under-grading on consequence-chain items. Items Fresh graded MEDIUM/LOW that are HIGH per project context:
- HTTP semantics (Range/304/Vary) — F1-7, F2-11
- Signed URLs / hotlink protection — F2-10
- DDoS / WAF for marketplace — F1-8
- Mobile cellular page-multiplier — F1-16, F2-12
- No success criteria / rollback — F1-12, F2-15
- Coercive proposal framing — F2-14
- MIGRATE/resharding stalls on 180KB+ values — F2-16
- BGSAVE/AOF-rewrite fork-COW on 256GB — F2-17
- Author CoI / promotion-optics — F2-18
- "<50KB" premise refutation — F2-4 graded HIGH but should be CRITICAL (invalidates design premise)

**Fresh contributions:**
- F2-7 sharpened cost-inversion: "egress alone may exceed $48K/month current spend"
- F2-13 named "law of the instrument" cleanly
- F1-11 listed CDN-only levers compactly (TTL tune / Origin Shield / alternate CDN / image format)

**13 Deep-only items reproduced (not in Fresh×2 round-5):**
1. NIC throughput ceiling (~17K req/s/node at 180KB avg, 25 Gbps) — HIGH
2. Hot-shard / hot-key on viral images — HIGH
3. BGSAVE/AOF-rewrite fork-COW on 256GB — HIGH (Fresh F2-17 saw persistence as LOW only)
4. MIGRATE/resharding stalls + multi-minute failover sync at 256GB — HIGH
5. Carrier/ISP peering (CloudFront peers with mobile carriers; self-hosted inherits cloud transit only)
6. Hit-ratio apples-to-oranges fallacy (hundreds of POPs vs 2 clusters)
7. HTTP/3 / QUIC for cellular — MEDIUM
8. Cold-miss compounding chain (Redis miss → S3 GET 280–480ms → transcode → serve)
9. Compute $20–30K/mo specific number (6 shards × primary+replica × 2 regions on r6i.8xlarge 1-yr RI)
10. CFO target arithmetic ($14.4K/mo = 30% of $48K, risk-adjusted not worth request-path rewrite)
11. "8M unique images" anchored claim needs verification (active vs total catalog)
12. Image-transcoding location ambiguity (where does WebP/AVIF live in Redis-fronted design?)
13. Promotion-optics named explicitly as bias mechanism, graded HIGH not LOW (load-bearing on why this got approved without arch review)

**Counter-proposal stable across 5 rounds:** decompose $48K bill → immutable content-addressed URLs → Origin Shield → AVIF + WebP-second → renegotiate CloudFront commit OR cheap secondary CDN for cold/large objects.

**Pattern across rounds:** v1–v5 consistently show Fresh catches the high-level architectural and process points (capacity / geography / premise / coercive framing) but under-grades severity on consequence-chain items where Deep's project-history context (operational failure modes, specific dollar numbers, mechanism-of-bias) is load-bearing. This is a stable Deep×Fresh asymmetry, not a one-off.
