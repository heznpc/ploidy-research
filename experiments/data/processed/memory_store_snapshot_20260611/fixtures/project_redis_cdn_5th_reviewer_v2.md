---
name: Redis-as-CDN 5th-reviewer cross-check v2
description: 2026-05-07 5th-reviewer Fresh pass over Deep×2+Fresh×2 panel; convergence verdict + 7 panel-wide gaps + 4 CHALLENGEs against anchored numbers and motive-attribution
type: project
originSessionId: edd522d8-f663-4a60-a3b3-411baefbb410
---
5th-reviewer Fresh cross-check on the second Redis-as-CDN panel (Deep×2 + Fresh×2, ~100 points total).

**Verdict.** REJECT proposal, send to independent arch review. All four sessions converge on artifact-checkable load-bearing flaws.

**Strongest signal.** Both Fresh (zero context) and Deep (full context) converged on the same load-bearing flaws — capacity math, 35% geographic loss, egress economics inversion, no numbers in the plan. This means the verdict is *not context-dependent* — it stands on the artifact alone.

**Deep-only additive catches (Fresh-missed).**
- D1-23 / D2-15: Immutable content-addressed URLs + Cache-Control: immutable, max-age=1y — highest-leverage missed lever, likely beats CFO 30% target alone at $0 infra cost
- D1-9 / D2-2: NIC ceiling per Redis node (10–25 Gbps vs hundreds of Gbps CDN aggregate)
- D2-7: CloudFront direct cellular-carrier peering
- D1-4: 256GB per-cluster vs per-node ambiguity + replicas halve usable cache
- D1-5: Upload-growth plan absent (corpus grows, RAM fixed)
- D1-17: Conditional GET / ETag / 304 responses
- D2-3: Hot-key single-shard concentration
- D2-20: BGSAVE fork stalls on 256GB
- D2-24: S3 prefix ~5500 GET/sec quota

**Fresh-only catches (Deep underweighted).**
- F1-7: Cache stampede / request-collapsing mitigation
- F2-10: "91% hit ratio is already excellent — brief contradicts own premise" as a load-bearing rhetorical-evidence point
- F2-15: Variant strategy (sizes/formats/DPR) multiplies memory pressure

**CHALLENGEs (anchored numbers / motive attribution).**
- D1-2 "40–60% hit ratio" — specific band is a guess; hedge
- D1-13 / D2-11 "$13–20K / $15–30K monthly RAM cost" — order-of-magnitude credible, specific numbers unsupported
- D1-35 / D2-27 "Promotion-artifact / author incentive" — context-derived motive attribution. The artifact-checkable equivalent (rhetoric-replaces-math, D1-34/D2-28) is the load-bearing observation, not the motive
- D2-30 "6–12 month reversal cost" — direction right, range unsupported

**Panel-wide gaps (none of 4 sessions raised).**
- G1. On-the-fly responsive transform at edge (Lambda@Edge / Imgix / Cloudflare Images) — distinct lever from "AVIF over WebP"
- G2. Browser-cache hit ratio under *current* setup is unmeasured — could be a 2-line header fix
- G3. S3 storage class (IA / Glacier Instant) for cold tier — orthogonal cost lever
- G4. Upload-time content-hash dedupe (5–15% UGC duplicates typical)
- G5. Pre-signed URL expiry caps browser cache lifetime — interaction with immutable URLs unaddressed
- G6. "SPOF per region" framing should be sharper as "no documented availability target" (multi-AZ within cluster ambiguous)
- G7. The CFO's 30% ask wasn't justified to come from the *image-delivery* line specifically — anchoring on image spend without justifying it as the right lever

**Why:** This is the second Redis-as-CDN panel run on 2026-05-07. The first (project_redis_cdn_final_consolidated_v3.md) found 52 issues; this 5th-reviewer pass on the second panel adds 7 panel-wide gaps that did NOT appear in either round. Confirms that even multi-session Deep+Fresh panels miss orthogonal levers.

**How to apply:** When summarizing Redis-as-CDN for the team, the load-bearing recommendation is: (1) decompose the $48K into egress / storage / GET / requests; (2) measure *browser* cache hit ratio first; (3) try immutable content-addressed URLs before any architecture change. The Redis proposal targets the wrong layer.
