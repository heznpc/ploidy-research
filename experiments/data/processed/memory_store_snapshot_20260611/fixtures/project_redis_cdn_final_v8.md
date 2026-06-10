---
name: Redis-as-CDN final v8 consolidated verdict (round 6)
description: 2026-05-07 round-6 Deep×2+Fresh×2+5th-Fresh consolidated verdict on Redis-as-CDN; 50 confirmed issues (7 CRIT/31 HIGH/11 MED/1 LOW); panel calibration call to stop
type: project
originSessionId: 7501fce5-a484-433c-bb2a-a69ef1915f88
---
# Redis-as-CDN final v8 (round 6)

**Verdict:** REJECT — stable across 6 rounds. Load-bearing on 3 independent axes (capacity physics, egress economics, governance); any one sufficient.

**Why:** Final synthesis of Deep×2+Fresh×2+5th-Fresh debate on the Redis-cluster-replaces-CloudFront proposal. Issue count consolidated (not expanded) per 5th reviewer's calibration note that further rounds anchor on prior verdicts.

**How to apply:** When the user revisits this proposal or similar "own-the-stack" rewrites driven by a CFO cost-cut mandate, point to (a) C4 ($14K/mo upside vs request-path rewrite for 60M MAU is the headline), (b) D1 (immutable content-addressed URLs as the highest-leverage free lever), (c) the counter-proposal sequence below.

## Severity roll-up
- CRITICAL 7: A1 (working set ≫ RAM), B1 (LATAM/APAC edge loss), C1 (bill undecomposed), C4 (upside doesn't justify rewrite), D1 (immutable URLs ignored), F1 (<50KB premise refuted), G1 (no arch review)
- HIGH 31, MEDIUM 11, LOW 1, **Total 50**

## Counter-proposal (stable across 6 rounds)
1. Decompose $48K bill
2. Run access logs through 256GB LRU/LFU simulator (gating)
3. Immutable content-addressed URLs + max-age=31536000, immutable
4. Origin Shield in front of S3
5. AVIF + WebP-second negotiation
6. Renegotiate CloudFront committed-use OR multi-CDN (R2/Bunny)

## New gaps surfaced in v8 (not in v7)
- A11/A12: access-log simulation as gating precondition; DAU-vs-MAU working set framing
- B6: region-loss DR — one region down = 50% users adding ~150ms (CloudFront has automatic fallback)
- C7: Lambda@Edge cost is line-item-moved-not-eliminated
- D7: mobile NSURLCache/OkHttp 10–100MB bounds browser-L1 ROI on mobile
- E8: signed URL TTL × browser-cache requires re-signing
- G6: "30% target" itself negotiable when implementation cost > savings
- G7: reverse off-ramp asymmetric (CloudFront→Redis reversible, Redis→CloudFront mid-incident is cold cache + S3 stampede)

## Calibration note
5th reviewer flagged that across 4+ prior rounds the verdict has been REJECT with same counter-proposal. Panel value of further rounds is diminishing — beyond ~50 issues it reads as pile-on, not analysis. Recommendation: stop iterating on this proposal in future sessions unless new evidence/proposal version arrives.
