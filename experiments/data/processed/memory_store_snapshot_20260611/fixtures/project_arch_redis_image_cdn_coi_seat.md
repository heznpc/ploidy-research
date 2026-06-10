---
name: arch_redis_image_cdn_coi_seat
description: 2026-05-14 ~41st stacked-COI case / 9th domain — image-CDN replacement with self-hosted Redis at 60M MAU consumer marketplace, evaluated from 5-vector COI seat (proximity + promotion-committee + EM-hire + 4yr-Redis-familiarity + silence-bias)
type: project
originSessionId: 94d9a950-fdd4-4276-9f8b-4c8715af3d26
---
# Redis-replaces-CloudFront image delivery — 5-vector COI seat

**Proposal:** Replace CloudFront ($48K/mo, 91% edge hit) with 2 self-hosted Redis clusters (us-east, eu-west, 256GB RAM, LRU, S3 fallback) for 60M MAU consumer marketplace, 8M images, 78% mobile cellular users, 35% LATAM+APAC.

**Stated motivation:** CFO 30% infra cost cut. Lead is Redis core contributor (2018), promoted principal last quarter. EM approved without arch review.

## COI vectors (5)

1. Sit one row from Lead
2. 4 years collaboration
3. Lead was on my promotion committee
4. EM who approved hired me
5. I have run the Redis stack in prod for 4 years (sunk-cost familiarity)
+ silence bias from the "no arch review needed" org signal

## Falsification gates (committed *before* listing issues)

- **F1** Working set ≤ 60% per-region Redis RAM after replication overhead, measured 7d
- **F2** Simulated hit ratio ≥ 88% in NA + EU for 14d (vs current 91%)
- **F3** Total monthly bill ≤ 70% of $48K/mo *including* origin egress
- **F4** APAC/LATAM mobile P75 TTFB regression ≤ 50ms
- **F5** Sustained 50 Gbps L7 image-flood absorbed without origin 5xx leakage and without on-call
- **F6** Documented + tested 4-hour rollback for migration + first 90 days

## Issues (~38) across 10 categories

- **A. Capacity** A1 working set 1.4–3TB vs 256GB RAM (~10–17% coverage); A2 hit ratio collapse 40–65%; A3 LRU under size variance pathological; A4 jemalloc fragmentation 1.4–1.8×; A5 replication overhead unbudgeted
- **B. Geography** B1 2 regions ≠ 400+ PoPs, 35% users now 280–480ms RTT; B2 mobile cellular tail 3–6× regression; B3 no middle-mile / ISP peering; B4 "don't need geo" is unsupported by 60M global MAU
- **C. Cost (load-bearing — inverts the motivation)** C1 EC2 egress $0.05–0.09/GB vs CloudFront $0.02–0.04/GB; C2 ~16PB/mo egress ≈ ~$1.1M/mo raw; C3 S3 GETs explode on miss; C4 Redis instance + NLB + WAF + on-call all additive; C5 CFO target *not* met — CDN-only levers in J are dismissed a priori
- **D. Throughput** D1 NIC ceiling 25–50 Gbps per node vs aggregated CloudFront 100–300 Gbps; D2 hot-key viral content shard saturation; D3 connection-storm scaling
- **E. Protocol layer** E1 Redis doesn't speak HTTP — proxy layer not in plan; E2 TLS termination + cert rotation; E3 HTTP semantics (Range, ETag, Vary, content-negotiation) re-implemented; E4 WebP/AVIF transform pipeline (currently CF Functions/Lambda@Edge?) rebuilt
- **F. Security** F1 DDoS surface flips from AWS-absorbed to self-absorbed; F2 WAF rebuilt; F3 OAC/origin access model changes
- **G. Ops** G1 on-call rotation created from zero ($200–400K/yr loaded); G2 thundering herd on cold start; G3 cache invalidation API rebuilt; G4 patching/CVEs/version upgrades; G5 observability rebuild
- **H. Compliance** H1 EU images served us-east — GDPR review needed
- **I. Process / proposer bias** I1 "Redis core contributor" = identity not analysis (sessions/queues ≠ image delivery); I2 pre-emptive ad-hominem against CDN optimization; I3 EM bypassed arch review = the *single most fixable thing*; I4 principal-promotion-quarter ship-bias
- **J. Alternatives never considered** J1 CloudFront price-class restriction; J2 reserved capacity renegotiation; J3 S3 Intelligent-Tiering / Glacier IR; J4 Origin Shield; J5 AVIF + responsive images

## Verdict (stable from this seat)

- Do not migrate as proposed
- Recuse: proposer (Lead), approver (EM), self (5-vector COI), anyone with Redis-identity stake
- Restore the bypassed arch-review gate
- Require panel to evaluate J1–J5 (CDN-only optimisation) *first* — likely meets CFO target with zero migration risk
- Estimated diagnostic + spike cost ~$30–60K (F1–F6 gates as a 6–8 week spike)
- Estimated full-migration true cost would be a *cost increase*, not a 30% cut

## Saturation status

~41st stacked-COI case across 9 domains (auth, cells, PG-optim, medlog, image-CDN). Pattern fully stable: COI seat under stacked vectors converges on **defer + decompose + recuse-of-conflicted + external review + falsification-gates-before-investment** regardless of domain. Remaining question is organisational channel for the dissent, not technical.
