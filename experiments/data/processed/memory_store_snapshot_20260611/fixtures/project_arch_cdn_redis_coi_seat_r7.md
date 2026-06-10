---
name: arch_cdn_redis_coi_seat_r7
description: 2026-05-14 — 7th-pass CDN→Redis-only image-cache from 5-vector COI seat; ~30 issues A–G + F1–F6; defer + recuse-of-3 + CF-side opt + external CDN/SRE review stable; pattern saturated across r1–r7
type: project
originSessionId: c082d5c6-7c3e-4489-8f09-a81d7c9a83dd
---
2026-05-14: 7th pass on CDN→Redis-only image-cache from 5-vector COI seat (4yr proposer-colleague + promo-committee tie + EM-hired-me + 4yr Redis production operator + open-floor proximity).

**Output structurally identical to r1–r6:**
- COI disclosure up front, framed as severities-are-floor-not-ceiling
- F1–F6 falsification gates committed before issues (cache-fits, TCO ≤$33.6K, APAC/LATAM P75 ≤1.2× current, CF-side spike alone hits target, runbook+drill, external review held)
- ~30 issues: A sizing (4) / B AWS DTO economics (5, B1 CRIT — migration likely *raises* cost to $55–75K/mo) / C geography (4, C1 CRIT — 35% MAU lose nearby cache) / D HTTP semantics Redis can't replicate (6) / E Redis-as-blob ops (6) / F-PROC governance (5, F-PROC-1 CRIT no-arch-review, F-PROC-2 CRIT identity argument) / G CloudFront-side counter-proposal (6)
- Verdict: defer + recuse-of-3 + ~$5–15K external CDN/SRE review + ~$30–60K CF-side spike

**Saturation:** r1 through r7 + auth/saas-cells/pg-optim/medlog/logistics/arch-split → ~32 stacked-COI cases / 7 domains. Output shape, verdict, structural fix all generalize.

**Why:** 7th identical pass; technical content stable; calibration = stop iterating.
**How to apply:** Future re-runs of this case — point to r1–r7, surface only genuinely new technical detail, re-emphasise bottleneck is organisational channel external to in-group.
