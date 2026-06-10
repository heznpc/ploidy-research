---
name: Redis-as-CDN Deep×2 → Fresh×2 cross-review v4
description: 2026-05-07 fourth Deep×2 pass on Fresh×2 Redis-as-CDN; 0 CHALLENGE, 3 SYNTHESIZE (browser-cache severity, authority-bias mechanism, cost-lever framing); 3 Fresh-unique catches (invalidation, transform pipeline, observability); ~26 Deep-unique items
type: project
originSessionId: d6ef0168-1cd3-4805-ad08-ab32a6dde580
---
2026-05-07. Fourth Deep×2 cross-review pass on Fresh×2 Redis-only image delivery proposal. Verdict stable across 4+ rounds — REJECT.

## Outcome (vs v3)
- 0 CHALLENGE.
- 3 SYNTHESIZE: browser-cache severity (MED→HIGH for immutable content-addressed URLs), authority-bias mechanism (Fresh stops at "ideology"; Deep names lead-as-poor-sole-evaluator), cost-lever framing (decompose $48K bill before architecture).
- ~30/39 AGREE.
- Fewer severity escalations than v3 — Fresh×2 in this round rated more items HIGH than v3 panels.

## Fresh-unique catches Deep×2 missed this round
1. Cache invalidation / DMCA / GDPR takedown (Fresh 1 #18, Fresh 2 #15).
2. Image transformation pipeline location unclear (Fresh 1 #20).
3. Observability regression (Fresh 1 #22, Fresh 2 #17).

## Deep-unique items reproduced from prior rounds
- NIC ceiling (binding capacity, not RAM).
- Carrier peering (cellular-latency mechanism).
- Egress is the wrong cost lever; multi-CDN (R2/Bunny ~17×); AWS PPA renegotiation; Origin Shield; AVIF.
- Hardware+ops $15–25K/mo unbudgeted.
- Range/206; Vary; conditional GET/304 inflating bill.
- BGSAVE fork COW; DR halving; MIGRATE per-key blocking; no request collapsing.
- DDoS Shield/WAF/edge compute/bot mitigation lost.
- No A/B canary; rollback risk + commit-tier forfeit; no SLO; "we know Redis" is category error.
- S3 5500 GET/prefix/s throttle ceiling.

## How to apply
Verdict (REJECT) stable across 4 review rounds. The 30% target is achievable via decompose-bill + Origin Shield + immutable URLs + AVIF + multi-CDN + AWS PPA — no Redis rebuild. Load-bearing axes Fresh consistently misses are NIC-bound capacity, carrier-peering mechanism, and the egress-vs-compute cost-lever framing. When synthesizing Redis-as-CDN-style panels, ensure these three axes appear explicitly in the Fresh seat brief or expect to add them in synthesis.
