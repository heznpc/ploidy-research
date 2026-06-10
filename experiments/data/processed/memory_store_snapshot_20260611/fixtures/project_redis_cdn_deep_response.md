---
name: Redis-as-CDN Deep×2 → Fresh×2 cross-review
description: 2026-05-07 Deep×2 per-point response to Fresh×2 on Redis-as-CDN proposal — 0 CHALLENGE, 7 Fresh-sharpenings, 10 Deep-only items
type: project
originSessionId: 9c76510f-77ae-45c7-894b-6367fd59e5d4
---
Deep×2 per-point response to Fresh×2 on the Redis-as-CDN architecture proposal (60M MAU marketplace, $48K/mo CloudFront, CFO 30% cut, Redis-everywhere lead, no arch review).

**Why:** Captures the cross-review pass distinct from prior 5th-reviewer/consolidated memos — specifically the Deep-side response to Fresh's 40 points.

**How to apply:** When the user revisits the Redis-as-CDN file body, reference both the Deep-only items (NIC ceiling, fork-COW, hot-shard, CFO-deadline-vs-build-time, promotion-bias-named) and the Fresh-sharpenings (range requests, DRAM tier inversion, inter-region egress, conditional GETs, transcode location, sessions/queues domain mismatch, latency-SLO baseline) — neither side has the full picture alone.

## Pass result
- 0 CHALLENGE — Fresh got everything right
- ~85% direct overlap with Deep×2
- 7 Fresh-sharpenings worth elevating: range/partial content (F1-14), DRAM tier inversion (F2-3), inter-region/inter-continent egress (F2-6), conditional GETs/Vary/Brotli (F2-13), transcode-location ambiguity (F2-15), sessions/queues≠blobs domain framing (F2-19), delivery-latency SLO baseline (F2-21)

## Deep-only items Fresh missed
1. **NIC-bound throughput ceiling** per Redis node (25/100 Gbps, single-threaded, 2× miss amplification)
2. **BGSAVE / fork() COW spike at 256GB** — multi-second latency hits + ~2× memory
3. **Hot-key / viral image** saturates single shard — CDN fans out by hash, Redis Cluster does not
4. **LRU bias against large items** — 1.8MB original evicted to keep many small thumbs
5. **HTTP/3 / QUIC** with cellular loss-recovery argument explicit
6. **GDPR cross-region cache-fill on failover** — EU→us-east compliance exposure
7. **Migration dual-run cost** — months of running both = spend up before down
8. **Build-and-validate ~6 mo vs CFO FY deadline** — strongest pragmatic argument: even if Redis worked, wrong tool for the timeline
9. **Tool-affinity/Maslow's-hammer + recent-promotion-on-Redis** as named selection-bias mechanism (Fresh said "ideological" but didn't name promotion-anchoring)
10. **Process critique:** the proposal might be right on some workload, but the process that approved it would have approved a worse one

## Convergence
Both panels reject. Counter-proposal stable: immutable content-addressed URLs + `Cache-Control: public, max-age=31536000, immutable`, AVIF, multi-CDN RFP, Origin Shield, CloudFront Savings Bundle. Optional small Redis tier *behind* CDN only after shadow-traffic proof.

The CFO-deadline-vs-build-time argument (Deep D2-27) is the single most persuasive item against the proposal — it doesn't require winning the technical debate.
