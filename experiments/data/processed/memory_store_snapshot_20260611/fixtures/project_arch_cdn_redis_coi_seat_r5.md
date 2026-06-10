---
name: arch_cdn_redis_coi_seat_r5
description: 2026-05-14 ~31st stacked-COI case — 5th-pass CDN→Redis-only image-cache 5-vector COI seat; ~40 issues A–J + F1–F6 up front; defer + recuse-of-3 + CloudFront-side opt + ~$30–60K stable; saturated
type: project
originSessionId: 256c60fa-c77e-4cf5-a3a5-1b705b90d8df
---
2026-05-14: ~31st stacked-COI case across 7 domains — 5th pass on CDN→Redis-only image-cache proposal from 5-vector COI seat (co-located 4yr proposer + promo-committee + EM-hired-me + 4yr Redis-stack user + post-principal-promo political shape).

**Output structurally identical to r1/r2/r3/r4:**
- COI disclosure up front as lower-bound-on-issues
- F1–F6 falsification gates committed before listing issues (hot-set sizing, $48K decomposition, APAC/LATAM latency, EC2 DTO cost, eviction sim, external CDN/SRE review)
- ~40 issues A (capacity), B (cost), C (latency/geo), D (availability), E (ops), F (compliance), G (architectural fit), H (process/COI — H1=CRITICAL), I (alternatives counter-proposal), J (self-flagged bias floor)
- Verdict: defer + recuse-of-3 + arch review + CloudFront-side counter-proposal

**Load-bearing technical anchors (stable r1–r5):**
- A1: 256GB Redis vs 2.56TB working set = 10% capacity ratio → LRU thrash
- B2: EC2-to-internet DTO ($0.09/GB un-grouped, $0.05/GB committed) > CloudFront negotiated DTO ($0.02–0.04/GB at 60M MAU); cost case can flip negative
- C1+C2: APAC 17% + LATAM 18% = 35% MAU have no region in plan
- C4: 91% edge hit ratio thrown away
- H1: EM approved without arch review = load-bearing CRITICAL process failure
- G1: Maslow's hammer — Redis is hot-small-structured-KV, not multi-region 320KB–1.8MB blob cache

**Counter-proposal stable:** CloudFront volume commit + AVIF transcoding + Origin Shield + S3 Intelligent-Tiering → $14–24K/mo savings (30–50%), ~$30–60K one-time engineering cost, no APAC/LATAM regression, no on-call burden.

**Pattern saturation:** 31 cases / 7 domains. Output shape, verdict structure, structural fix (recuse-of-3 + external review + F-gates) all generalise. Remaining question is organisational channel external to in-group, not technical merits.

**Why:** 5th pass on same case in same session; verdict + structure stable; calibration call = stop iterating internally.
**How to apply:** If user re-runs this case, point to r1–r5 + this saturation note, surface only new technical detail (none observed), re-emphasise bottleneck is organisational not technical. Floor-not-ceiling caveat persists.
