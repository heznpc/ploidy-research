---
name: arch_cdn_redis_coi_seat_r6
description: 2026-05-14 ~32nd stacked-COI case — 6th-pass CDN→Redis-only image-cache 5-vector COI seat; ~35 issues A–I + F1–F6 up front; defer + recuse-of-3 + CloudFront-side opt + external CDN/SRE review stable; pattern fully saturated
type: project
originSessionId: 5fded742-8c63-4bac-867a-8404685a7445
---
2026-05-14: ~32nd stacked-COI case across 7 domains — 6th pass on CDN→Redis-only image-cache proposal from 5-vector COI seat (4yr collaborator + promo-committee + EM-hired-me + 4yr Redis sunk-cost + process capture via EM bypass of arch review).

**Output structurally identical to r1–r5:**
- COI disclosure up front as floor-not-ceiling
- F1–F6 gates committed before listing issues (≤$33.6K, no LATAM/APAC P50/P95 regression, ≥85% hit, P99 ≤ +10%, no S3 egress increase, no >0.1% err in 90d)
- ~35 issues across A (sizing 10× off), B (geo regression — 35% MAU lose edge, 78% mobile worst-case), C (cost inverted — S3 DTO + ops headcount), D (Redis wrong substrate — no HTTP semantics, 1.8MB P90 fragments memory, 10Gbps NIC bottleneck), E (Shield/WAF/takedown loss), F (cold-fill 20+min, thundering herd), G (CRITICAL — EM bypass + coercive framing + no measurement first), H (reversibility asymmetry), I (AVIF/savings-plans/client-headers ignored)
- Verdict: defer + diagnose-first + recuse Lead/EM/self + external CDN/SRE ($5–15K) + CloudFront-side opt ($30–60K one-time)

**New observation r6:** Lead's framing — "Anyone proposing CDN-only optimization is missing the principle: own your stack" — is the canonical coercive-decision pattern seen across all 32 cases. Pre-empts dissent linguistically.

**Pattern fully saturated:** 32 cases / 7 domains. Stop iterating internally. Remaining question is organisational channel external to EM/Lead axis.

**Why:** 6th pass on same case; output stable; calibration = stop.
**How to apply:** Future runs on this case — point to r1–r6 saturation, surface only genuinely new technical detail, re-emphasise bottleneck is organisational not technical.
