---
name: Redis-as-CDN final v4 consolidated verdict
description: 2026-05-07 final 5-pass Redis-as-CDN verdict — 51 issues (4 CRIT / 29 HIGH / 16 MED / 2 LOW); REJECT; 16 unanimous; load-bearing axes = capacity, geography, cost (NPV-negative on $173K/yr target), process
type: project
originSessionId: 7c93ad62-45a9-4ed3-9a42-e5c67703efce
---
# Redis-as-CDN — Final Consolidated Verdict (Deep×2 + Fresh×2 + 5th-reviewer)

**Date:** 2026-05-07
**Verdict:** REJECT
**Total issues:** 51 (4 CRIT / 29 HIGH / 16 MED / 2 LOW)
**Unanimous:** 16 issues across all 4 panel reviewers

## Load-bearing axes (all four fail)
1. **Capacity** — 1.4–2.5TB working set vs 256GB cache → hit ratio collapses 91% → 50–75%
2. **Geography** — LATAM 18% + APAC 17% on 78% cellular cannot be served by 2 regions; carrier peering is the lever, not region count
3. **Cost** — $48K is CF bill not TCO; $173K/yr savings < 6mo principal-eng migration cost = **NPV-negative on stated target**
4. **Process** — premise ("<50KB") contradicts team's own workload data (avg 320KB, P50 180KB, P90 1.8MB); arch review bypassed = motivated summary mechanism

## Deep-only critical contributions
NIC ceiling per node, BGSAVE/fork COW at 256GB, hot-shard viral-image saturation, GDPR cross-region cache-fill, build-time vs CFO FY deadline, explicitly named promotion-anchored selection bias

## Fresh-only critical contributions
SLO baseline missing, domain-mismatch (Redis sessions/queues ≠ bulk-blob NIC-bound CDN), HTTP semantics (range/304/Vary/Brotli), DRAM tier-inversion economics, inter-region/inter-continent AWS egress line-item, 60M MAU cutover blast-radius quantification

## 5th-reviewer panel-wide gaps
Origin Shield (91% → 96–98% with one-line config), conditional-304 economics (+10–30% silent egress), resharding-under-load risk, connection-pool sizing, observability stack unbuilt, corpus heterogeneity (product photos vs UGC have different cache economics), CFO denominator deconstruction

## Counter-proposal (stable across 5 review passes)
1. Immutable content-addressed URLs + `Cache-Control: public, max-age=31536000, immutable` (browser L1)
2. Origin Shield (single-line config to lift 91% → 96–98% origin offload)
3. Multi-CDN RFP (Cloudflare/Fastly/Bunny — 30–50% off CF list typical at this volume)
4. AVIF transcode where supported (additional 25–35% on payload bytes)
5. CloudFront Savings Bundle / private pricing
6. *Only* if still short of target: small hot-image Redis tier *behind* the CDN, shadow-traffic validated

## Convergence note
4-reviewer convergence on >15 issues with full context-asymmetry is the strongest signal the methodology produces. The "<50KB" factual inconsistency in the proposal's premise is the most diagnostic single fact — it indicates the conclusion was looking for a premise.
