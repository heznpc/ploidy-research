---
name: arch_cdn_redis_coi_seat_r9
description: 2026-05-14 — 9th-pass CDN→Redis 4-vector COI seat; ~30 issues A–I + F1–F6 gates up front; defer + diagnose-first + negotiate-CF + evaluate-R2 + recuse-of-3 + external review stable; saturated
type: project
originSessionId: 34cb6273-8cef-45ad-b1e8-ac95c4de4ff8
---
2026-05-14: 9th-pass CDN→Redis image-cache eval.

**Seat COI vectors**: deskmate Lead 4yr, Lead on my promo committee, EM hired me, 4yr user of pre-existing Redis-for-sessions/queues stack. Net: under-calls Redis-specific risk; under-calls Lead's tool-affinity bias.

**Case shape**: 60M MAU, $48K/mo CloudFront+S3 image delivery (91% edge hit, 280ms NA / 480ms APAC cold-start). Lead (Redis-OSS-contributor 2018, fresh principal promo) proposes 2 × 256GB Redis cluster fronting S3, NA+EU regions only. EM ("he's right; we own Redis ops") approved without arch review. CFO wants 30% off.

**~30 issues, 9 categories (stable across r1–r9)**:
- A. Capacity (HIGH): 512GB ≈ 15–20% of ~2.5TB+ raw WS; LRU thrashes on mobile-photo long-tail; no shadow-replay model
- B. Geo (HIGH): LATAM+APAC = 35% MAU lose nearest edge; cellular RTT amplification
- C. Workload misread (HIGH): plan says "<50KB" but avg 320KB / P50 180KB post-WebP / P90 1.8MB
- D. Protocol gap (HIGH): Redis≠HTTP origin; no HTTP layer, WAF, DDoS, signed-URL, range, ETag in plan
- E. Redis-for-large-values (HIGH): single-thread + per-node egress ~1–2Gbps bottleneck; fragmentation; big-key replication stalls; restart→thundering herd; LRU misfit (LFU better)
- F. Economics (HIGH): dominant cost is internet egress (unchanged by Redis tier); EC2 egress ≈ CF egress at volume; CF private pricing not negotiated; Cloudflare R2 zero-egress not evaluated
- G. Ops (HIGH): new tier-1 failure domain, on-call burden delta
- H. Process (HIGH): no arch review, EM rationale not architectural, principal+OSS-identity bias on Lead, my COI stacked
- I. Falsification gates F1–F6: shadow-replay hit≥85%, audited egress model ≥30% saving, APAC/LATAM P95≤current, CF private quote on file, R2/Fastly quote on file, external CDN reviewer sign-off

**Verdict (stable r1–r9)**: defer Redis-only plan → diagnose-first (30-day log segmentation) → pull cheap levers (CF commit pricing, AVIF, Origin Shield, TTL, responsive images) → quote Cloudflare R2 + commodity CDN → only if 1–4 fail, consider edge POPs (not 2-region clusters) with non-Redis-identified design owner. Recuse Lead from sign-off, EM from review chain, self from technical decision. External CDN/edge reviewer mandatory.

**Why load-bearing**: stacked-COI seats systematically under-call risk on tools they identify with; structural fix is recusal-of-3 + external review channel, not "be more objective."

**Pattern saturation**: ~53rd stacked-COI case / 10 domains; output structurally identical to r1–r8. Stop iterating internally; remaining Q is organisational channel external to the EM who approved without review.
