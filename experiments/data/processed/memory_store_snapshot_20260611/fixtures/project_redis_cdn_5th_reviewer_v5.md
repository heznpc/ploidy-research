---
name: redis-cdn 5th-reviewer v5
description: 5th 5th-reviewer Fresh pass cross-checking Deep×2 Redis-as-CDN panel; 0 strict CHALLENGEs, 4 anchored-number hedge-flags, 14 Deep-only catches confirmed, 5 Fresh-only catches Deep under-weighted
type: project
originSessionId: a51a52b2-b9c7-45ba-b6c4-e8561c7528e6
---
2026-05-07: 5th Fresh-side cross-review of Deep×2 (Redis-as-CDN proposal, round 8).

**Verdict alignment:** REJECT confirmed. Counter-proposal stable across 8 rounds.

**Deep-only items confirmed valid (Fresh would have missed):**
1. NIC ceiling binding, not RAM (25Gbps → 17K img/s @ 180KB)
2. Hot-shard viral concentration (cluster mode doesn't help)
3. Fork-COW BGSAVE OOM risk on 256GB
4. S3 prefix throttle = 5,500 GET/s/prefix → cascade
5. Carrier peering loss (T-Mobile/Vodafone/Jio)
6. Browser-L1 via immutable content-addressed URLs (decision-independent)
7. Blast-radius coupling with sessions/queues (project-context-only)
8. No experiment/kill criteria gate
9. No off-ramp plan
10. COI governance stack (author=ex-promo, approver=hiring manager)
11. "Sessions/queues ≠ CDN" domain transfer mismatch
12. Parts-count inversion (LB+HTTP+Redis+S3 > CloudFront)
13. Fronting-tier still required (Redis isn't HTTP)
14. HTTP semantics: range, 304/conditional GET, Vary

**Fresh-only catches Deep under-weighted:**
1. Size-cutoff tiered policy (small RAM / large CDN+S3) — concrete remediation
2. 30% target is org-wide, image is $576K/year line item — risk/reward miscalibration
3. HTTP/3/QUIC/Brotli protocol-stack regressions (mobile-relevant)
4. Storage-$/GB ratio (RAM ~50–100× S3) — tier-cost framing
5. "Right tool for the job" principle inversion (content-of-framing as evidence, no motive attribution needed)

**Anchored-number hedge-flags (not strict CHALLENGEs):**
- D1-8: "3–10× egress increase" while admitting bill not decomposed — internally inconsistent
- D1-19: "$300–500K build cost" — over-confident anchor
- D1-3: "~900 PoPs" — actually 600+; verify
- D2-25: 99.9%/99.5% SLO anchors — direction right, anchors not derived

**Pattern observation across 8 rounds:**
- 5 of 8 rounds independently rediscover the immutable-URL browser-L1 lever; never first-listed in counter-proposal — chronic placement bias
- Severity-floor under-grading by Fresh on consequence-chain items recurs (memory_redis_cdn_deep_response_v3, v5)
- Motive-attribution items (promotion timing, lead identity) consistently better-framed when grounded in observable rhetoric (Fresh-1 #13, D1-20) than in biographical attribution (D2-3)

**How to apply:**
- For Redis-as-CDN-class proposals (large-blob HTTP delivery via in-memory KV), the first three checks should be: (1) decompose the bill, (2) ship immutable URLs + long Cache-Control as decision-independent, (3) verify NIC ceiling against peak fanout. These three alone disqualify or de-scope most such proposals before architecture review.
- When 5th-reviewer Fresh sees "promotion timing" / "lead identity" arguments, prefer the rhetoric-as-evidence framing; flag biographical framing as motive imputation.
- Anchored cost multipliers ("3–10×") should be hedged when the input data ("bill not decomposed") is admitted unknown in the same review.
