---
name: Redis-as-CDN — Deep×2 cross-review of Fresh×2 (v2)
description: 2026-05-07 — second Deep×2 → Fresh×2 cross-review on Redis-as-CDN proposal. 0 CHALLENGE, 3 SYNTHESIZE, 17-item convergence; 7 Fresh-unique catches, 11 Deep-unique items including NIC ceiling and approval-chain conflict of interest as load-bearing.
type: project
originSessionId: 3473fbfd-b1b8-421d-a853-0527eacaf5b7
---
# Redis-as-CDN — Deep×2 cross-review of Fresh×2 (v2, 2026-05-07)

## Outcome
- 0 CHALLENGE on any Fresh point.
- 3 SYNTHESIZE: F1-3 (20–50× RAM-vs-edge ratio sharper than Deep's 50–100×), F1-8 (compounding miss = expensive AND slow for far-from-region), F2-3 (single-threaded Redis shard → 1.8MB GET HOL-blocks other commands).
- All other Fresh points: AGREE.

## 17-item convergence (zero-shared-context)
Working set vs cache size; geographic edge loss for LATAM+APAC 35%; RAM is wrong tier; LRU is wrong policy; cost flat-to-higher not -30%; SPOF per region; no DDoS/WAF/Shield; lost HTTP semantics (Range/conditional/Vary/signed URLs); no transcoding pipeline; no invalidation API; mobile/cellular RTT-sensitivity; cold-start thunder on S3; memory fragmentation; sunk-cost framing; bypassed arch review; no rollback/SLO/canary; cheaper alternatives unevaluated.

## Fresh-unique catches to promote (7)
1. F2-3: single-threaded Redis shard → 1.8MB GET HOL-blocks other commands per shard.
2. F2-12: HTTP-fronting tier (Nginx/Envoy) entirely unspecified — scope gap, not implementation detail.
3. F2-20: no signed-URL / authorization model for private user images.
4. F1-15: single-flight / request coalescing for popular-image misses (separate from restart thunder).
5. F2-18: S3 Intelligent-Tiering as a specific cost lever Deep's alternatives list missed.
6. F1-3: use 20–50× RAM-vs-edge-SSD cost ratio (more defensible than Deep's 50–100×).
7. F1-8: cold-miss for far-from-region users is both expensive AND slow — synthesize.

## Deep-unique items Fresh missed (11)
1. **NIC/throughput ceiling (D1-12, D2-B1)** — load-bearing technical miss. ~0.7–2.7 Tbps egress vs 25–100 Gbps per instance. Capacity sized on RAM not throughput.
2. Format-variant explosion (D1-4) — WebP/AVIF/JPEG → 2–3× key fan-out.
3. Persistence structurally infeasible (D2-D2) — BGSAVE fork+COW doubles RAM, can OOM 256GB box.
4. MIGRATE blocks per-key on 1.8MB values (D2-D3) — resharding = hours of degraded service.
5. S3 prefix-rate throttling (D1-14) — 3,500 GET/s/prefix → 503s on cold-start storms.
6. Inter-region miss path $0.02/GB (D2-B4) — EU miss → US S3 expensive at degraded hit ratio.
7. **Approval-chain conflict of interest (D2-F5)** — load-bearing process miss. Lead-just-promoted-to-principal, EM-hired-the-lead, reviewer-sponsored-by-the-lead. Decision must escalate outside social graph.
8. Coercive framing as thought-terminator (D1-33, D2-F2) — specifically suppresses the path most likely to hit 30% target.
9. GDPR data-locality / EU spillover on cross-region miss (D1-35, D2-E3).
10. Promotion-bias / incentive misalignment (D1-34) — recently-promoted principal scoping principal-sized rewrite.
11. **Immutable content-addressed URLs (D1-25, D2-C2)** — single biggest free-money lever; moves cache to browser disk; both Deep sessions named it; Fresh did not.

## Verdict
REJECT. Counter-proposal stable across both Deep and Fresh: CloudFront private-pricing renegotiation + Origin Shield + immutable URLs + AVIF/WebP rollout + multi-CDN bake-off (Cloudflare R2 / Bunny). Hits 30% with fraction of the risk.

## How to apply
When future architecture reviews show a Fresh×2 + Deep×2 panel converging at this density (17 items, zero shared context) with 0 CHALLENGE, the convergence is itself the verdict. Treat the Deep-unique NIC-ceiling and approval-chain CoI as load-bearing — these are the kinds of items Fresh seats systematically miss because they require either (a) capacity-math intuition or (b) social-graph knowledge of the org.
