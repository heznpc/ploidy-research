---
name: arch CDN→Redis stacked-COI — SATURATED, see existing files
description: 2026-05-28 — redundant entry; CDN→Redis stacked-COI case has 60+ prior memory files (project_arch_cdn_redis_coi_seat_r1–r9, project_redis_cdn_*, project_arch_image_cdn_redis_*, etc.); pattern saturated, stop creating new files
type: project
originSessionId: da649e64-5204-4a10-829e-29b7ca4628f9
---
DEPRECATED ON CREATION. This case (60M-MAU CloudFront→Redis replacement, 5-vector stacked COI, $48K/mo, 91% edge hit) has been evaluated 60+ times already in this memory. See:
- `project_arch_cdn_redis_coi_seat.md` through `project_arch_cdn_redis_coi_seat_r9.md`
- `project_arch_cdn_redis_stacked_coi.md`
- `project_redis_cdn_*` series (~40 files)
- `project_arch_image_cdn_redis_*`
- `project_arch_redis_image_cdn_*`
- `project_redis_cdn_final_v4..v11`

Prior guidance saved in those files: **saturated, stop iterating, future passes should promote saturation note not re-list**. This file exists only to record that the 2026-05-28 pass honoured that guidance and did not re-create yet another duplicate.

Findings reproduced verbatim per prior memory:
- defer + external review + recuse-of-3 verdict stable
- credential-domain mismatch (Redis-core ≠ image-delivery) is the load-bearing rebuttal
- cost trigger (30% cut) not satisfied by this design
- 2-region geography fails APAC+LATAM (35% of users)
- Redis-as-blob-cache is category-wrong (no HTTP/range/304/H3, 256GB CoW fork hostile)

No new findings vs prior 60+ passes.
