---
name: Redis-as-CDN final v11 verdict (round 9)
description: 2026-05-07 — Final round-9 consolidated Redis-as-CDN verdict (56 issues: 3 CRIT/33 HIGH/17 MED); 1 strict CHALLENGE (Deep→Fresh on hit-ratio axis), 5 SYNTHESIZE escalations; counter-proposal stable; calibration says stop iterating
type: project
originSessionId: cb4b6dbb-e717-4e0a-9462-b2295d0673c9
---
## Round-9 final consolidated verdict on Redis-as-CDN proposal

**Verdict: DO NOT PROCEED** (stable across 9 rounds, 0 bidirectional CHALLENGE).

**Tally: 56 confirmed issues**
- 3 CRITICAL (all governance: no review, single-author/rubber-stamp, promotion-CoI)
- 33 HIGH
- 17 MEDIUM
- 1 strict CHALLENGE (Deep→Fresh F1-20: hit-ratio framing is wrong axis — money is in bytes×rate)
- 5 SYNTHESIZE escalations (range-requests MED→HIGH, TLS-handshake amplification, DDoS Shield, S3 free-transfer, overhead enumeration)

**Source breakdown**
- Both found: 26
- Deep-only: 26 (NIC ceiling, fork-COW, hot-shard, carrier peering, immutable-URL browser-L1, AVIF/srcset, Origin Shield, CF commit renegotiation, single-flight, sessions+queues+blobs collision, RSALv2 license, promotion-CoI mechanism, coercive framing as process flag, etc.)
- Fresh-only: 4 (CloudFront-S3 free-transfer specifically, jemalloc-frag, TLS-handshake-2-3× sharpening, cross-region cache consistency stale-duration distinct from invalidation)

**Load-bearing chain**: A1 (working-set ≫ RAM) + A5 (NIC ceiling) + B1 (geography) + B4 (carrier peering) + C3 (CF→S3 free-transfer) + C4 (egress retail) + E4/I1 (immutable-URL browser-L1) + H1–H3 (governance).

**Counter-proposal (stable 9 rounds)**: decompose-bill → CloudFront commit renegotiation + Origin Shield + immutable URLs + AVIF/responsive + optional R2/Bunny multi-CDN + architecture review with external reviewer + recusal.

**Recurring panel-wide blind spots** (Fresh systematic gaps): browser-L1 / immutable URLs (missed 6/9 rounds), carrier peering (7/9), NIC ceiling (7/9), promotion-CoI as named mechanism (8/9), license risk (7/9).

**Recurring Fresh systematic strengths**: CloudFront-S3 free-transfer (sharper than Deep), jemalloc fragmentation specificity, TLS-handshake amplification on cellular, "you've reinvented a CDN poorly" framing.

**Calibration**: marginal information per round → 0 by round 7-8; round 9 reproduces same Deep-only set + same Fresh-unique set. Stop iterating.

**Why this matters for the paper (project_session_evidence)**: this is a textbook intentional-context-asymmetry win — Deep contributes ~10 panel-wide gaps each round that Fresh structurally misses (because they require knowing the proposer's promotion history, the prior cluster's operational profile, the contract terms, etc.), and Fresh contributes sharper compact framings that Deep over-elaborates. Bidirectional 0-CHALLENGE across 9 rounds is the convergence signal.
