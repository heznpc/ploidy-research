---
name: Redis-as-CDN final consolidated verdict v3 (Deep×2+Fresh×2+5th)
description: 2026-05-07 final v3 consolidated verdict on Redis-only image-delivery proposal — 52 confirmed issues (4 CRIT/32 HIGH/14 MED/2 LOW); REJECT; counter-proposal stable across 3 review rounds
type: project
originSessionId: c1f80863-5cd3-49ef-86d4-33e97b668b97
---
2026-05-07 — Redis-as-CDN proposal final consolidated verdict (Deep×2 + Fresh×2 + 5th-reviewer Fresh).

**Verdict: REJECT AS WRITTEN.** Convergence: 0 CHALLENGE on direction, 7 SYNTHESIZE (mostly severity escalations), 1 quantitative correction.

**Why:** Cost premise inverts (egress 5–15× current bill at 8 PB/mo ≈ $400–680K/mo vs current $48K), working set 5–10× cluster RAM, 35% of MAU (LATAM+APAC) loses geographic proximity, and proposal was approved without architecture review at 60M MAU customer-facing path.

**How to apply:** Use as canonical record for arch-review meta-experiments. The 4 CRITICAL load-bearing issues are: (C1) egress cost inversion, (C2) working-set/RAM mismatch with fragmentation+key-cardinality amplifiers, (C3) geographic regression, (C4) governance failure (no review + reviewer-as-friend).

**Counter-proposal stable across all rounds:**
1. Decompose the $48K bill first (requests vs egress vs origin vs invalidation) — Fresh-unique prerequisite (F2-17).
2. Enable CloudFront Origin Shield + tiered cache — single-flag, often hits 30% alone (5th-reviewer).
3. AVIF + immutable content-addressed URLs (`/img/<hash>.webp` + `Cache-Control: max-age=31536000, immutable`) — moves repeat views to browser L1 (Deep-unique D2-21).
4. CloudFront committed-use OR migrate to Cloudflare R2 / Bunny / Fastly (zero or near-zero egress) — Fresh-unique (F2-18).
5. Any one of (2)–(4) likely hits 30%; combining two leaves headroom.
6. Require architecture review before any image-delivery change.

**Differential catches worth remembering:**
- **Fresh-unique:** LFU vs LRU policy (F2-2 — long-tail content needs `allkeys-lfu`, proposal inherited default), decompose-the-bill-first (F2-17 — sharpest single point in the panel), R2/Bunny/Fastly named alternatives (F2-18), DMCA/CSAM legal framing on invalidation (F2-10), no-HA-spec-gap framing (F1-4/F2-8 — Deep covered consequence not gap).
- **Deep-unique:** Browser L1 immutable URLs (D2-21 — load-bearing alternative the proposal hides), NIC saturation 25 Gbps = 3.1 GB/s per node (D2-7), single-shard hot-key under virality (D1-19/D2-8), S3 5,500 GET/s/prefix throttle ceiling (D1-17/D2-3), variant cache-key cardinality 12–150M (D1-16), no-rollback/dual-run/canary (D1-25/D2-22), no success criteria / kill-switch (D2-30), APAC data residency (D2-25), connection-storm from cellular handoffs (D2-24), reviewer-as-friend / promotion dynamic (D2-29).
- **5th-reviewer-unique additions:** Origin Shield as the single-flag answer (E4), anycast vs DNS-geo routing (E3), HTTP/2 connection coalescing on image-heavy pages (E1), HTTP 103 Early Hints (E2), MAU vs DAU vs sessions denominator caveat on cost models (E6), bot/crawler 100% bypass cost (E7), inter-AZ replication $0.01/GB (E9), dual-run period itself doubles bill (E10).

**Quantitative correction:** D2-9 estimated 270 TB/mo egress = $13–23K/mo. Arithmetic: 60M × 25 imgs/day × 180KB × 30d = 8.1 PB/mo, not 270 TB. D1-4's 5–8 PB/mo and $250–700K/mo is the canonical figure (off by ~30× from D2-9). Both Deep seats agreed on direction; one made an arithmetic slip the 5th reviewer caught.

**Session-evidence note:** This is the 7th major arch-review where Deep+Fresh asymmetry surfaced material deltas — Fresh-unique catches (LFU policy, decompose-bill-first, R2/Bunny named alternatives) would have been missed by Deep×2 alone; Deep-unique catches (browser L1 immutable URLs, NIC ceiling, S3 prefix throttle, rollback gap) would have been missed by Fresh×2 alone. 5th-reviewer Fresh added 8 panel-wide gaps neither pair caught.

Counts: 52 confirmed issues, 4 CRITICAL, 32 HIGH, 14 MEDIUM, 2 LOW.
