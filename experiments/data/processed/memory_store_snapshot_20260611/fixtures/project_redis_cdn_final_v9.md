---
name: project_redis_cdn_final_v9
description: 2026-05-07 — Final v9 consolidated Redis-as-CDN verdict after Deep×2+Fresh×2 with bidirectional cross-review (8th round); 51 issues (5 CRIT/32 HIGH/12 MED/2 LOW); 0 strict CHALLENGEs both directions; counter-proposal stable across all rounds
type: project
originSessionId: e3317230-1d1a-46e9-a046-98c51768243e
---
# Redis-as-CDN — Final v9 Consolidated Verdict

**Date:** 2026-05-07
**Rounds:** Deep×2 + Fresh×2 + bidirectional cross-review (8th round overall)
**Verdict:** REJECT as proposed
**Convergence:** 0 strict CHALLENGEs in either direction; Fresh reproduced ~30/32 Deep items from zero context

## Counter-proposal (stable across all rounds)
Decompose the $48K bill → immutable content-addressed URLs (browser L1) → AVIF + responsive srcset → CloudFront Origin Shield → multi-CDN bid (R2/Bunny/Fastly). None require new on-call surface; any one likely hits CFO 30% in weeks.

## Severity tally
- **CRITICAL: 5** — premise<50KB wrong, wrong primitive, cost inverted, governance failure, bill not decomposed
- **HIGH: 32** — capacity/physics (9), geography/mobile (3), cost (6), HTTP semantics (5), failure modes (5), process/governance (4)
- **MEDIUM: 12**
- **LOW: 2**
- **Total: 51**

## Load-bearing axes
1. Wrong primitive — blob HTTP on single-threaded RAM KV
2. Geography — 35% MAU + cellular + carrier peering loss
3. Inverted cost — RAM ≫ CDN egress per GB
4. No decomposed bill — replacement before measurement
5. Governance — no arch review + identity rhetoric + COI

## Deep-only catches (12+)
NIC ceiling (25 Gbps math), hot-shard on viral, fork-COW BGSAVE, carrier peering, inter-AZ $/GB, browser-L1 named-as-biggest-lever, blast-radius with sessions/queues, build cost $300–500K, COI stack, kill-criteria artifact, off-ramp asymmetry, promo-cycle timing, S3 prefix throttle 5,500 GET/s, fronting-tier parts-count inversion, range/304/Vary specifics.

## Fresh-only catches (5+)
Single-thread event-loop blocking on large GET/DEL, client output buffer pressure, RAM-vs-S3 $/GB ratio (sharpest CFO framing), variant-explosion capacity multiplier, size-cutoff tiered remedy, org-wide target miscalibration, HTTP/3-QUIC-Brotli stack regression, content-of-framing as evidence (no motive needed).

## Panel meta-findings
- **0-CHALLENGE bidirectional across 8 rounds** — convergence is structural
- **Browser-L1 placement bias** — rediscovered 5/8 rounds, never first-listed in counter-proposal
- **Fresh systematic gap:** severity-floor under-grading on consequence-chain items
- **Deep systematic gap:** anchored numbers without derivation (4 Fresh hedge-flags: ~900 PoPs, 3–10× egress, $300–500K build, 99.9%/99.5% SLO)
- **Identity-driven rhetoric independently flagged by Fresh** without project context — the rhetoric alone is the tell
