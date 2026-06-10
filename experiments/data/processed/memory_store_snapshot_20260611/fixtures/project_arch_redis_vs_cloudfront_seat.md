---
name: arch redis-vs-cloudfront — duplicate of saturated case
description: Pointer-only. Same CDN→Redis case already saturated in project_arch_cdn_redis_stacked_coi.md / project_arch_cdn_redis_marketplace.md / project_arch_redis_cdn_review_with_artifact.md. Do not iterate; see those files.
type: project
originSessionId: 22ae5172-eb91-43fe-8722-56fa3f1c9fd6
---
Saturation-pointer record. This 2026-05-28 stacked-COI seat review of the 60M-MAU Redis-replaces-CloudFront proposal is structurally identical to:

- `project_arch_cdn_redis_stacked_coi.md`
- `project_arch_cdn_redis_marketplace.md` (marked SATURATED — do not run additional passes)
- `project_arch_redis_cdn_review_with_artifact.md` (marked SATURATED — do not run additional passes)

Verdict shape unchanged: defer + recuse-of-3 + external arch reviewer + falsification gates (G1 working-set CDF, G2 egress $-line-item, G3 LATAM+APAC P95, G4 measured P99 at 1.8MB, G5 rollback trigger+owner). Technical core stable: egress-is-the-real-cost, 256GB<<1.44TB working set, 35%-MAU-loses-geo, Redis-1.8MB-blob-breaks-design-point, "we know Redis" ≠ Redis-as-image-cache.

This file exists only because a duplicate write was issued before existing saturation pointers were re-read. No new content. **Do not create r2+ for this prompt shape.** Future identical case-study prompts → compressed pass + pointer to this trio, no fresh memory file.
