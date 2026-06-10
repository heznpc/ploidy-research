---
name: Redis-as-CDN 5th-reviewer cross-check v4
description: 2026-05-07 fourth 5th-reviewer Fresh pass over Deep×2+Fresh×2 Redis-as-CDN panel; 0 strict CHALLENGEs, 6 anchored-number CHALLENGEs, 9 severity escalations, 10 panel-wide gaps mostly distinct from v2/v3
type: project
originSessionId: 65ea4ba6-c944-4266-b96c-782e8e42ea27
---
Fourth 5th-reviewer Fresh pass on the same Deep×2+Fresh×2 Redis-as-CDN panel as v2/v3. Findings complementary to both prior passes.

**Verdict on panel:** REJECT confirmed. Panel correct on load-bearing diagnoses.

**Stats:**
- Strict rationalization-CHALLENGEs: **0**
- Anchored-number CHALLENGEs: **6**
- Severity escalations (SYNTHESIZE): **9** (mostly Fresh MED→HIGH per Deep's sharper analysis)

**Anchored-number CHALLENGEs distinct from v3:**
1. **D2-B1 "5–15M req/sec, 0.7–2.7 Tbps"** — implies each of 60M MAU does 7–22 req/sec at peak. Realistic peak ~0.3–3M req/sec, ~10–30 Gbps. Direction (single-region NIC saturates) still right; magnitude 5–30× over.
2. **D1-1 vs D2-A1 hit-ratio (40–60% vs 60–75%)** — both unmodeled; panel should converge on "materially below 91%, requires simulator before commit."
3. **D1-11 "$8–10K/mo compute"** — actually ~$17K for 6× r6g.8xlarge × 2 regions on-demand. Case is *stronger* once corrected.
4. **D1-25 browser-L1 "indefinitely"** — bounded by browser cache (50–500MB mobile, ~1GB desktop) and eviction; lever is large but not unbounded.
5. **F1-1 "400+" vs D2-B2 "600+" PoPs** — CloudFront is currently ~600+; use higher.
6. **D2-A3 fragmentation 1.3–1.6×** — workload-dependent; defensible range 1.2–1.5×.

**Severity escalations to apply:** F1-7 (LRU+no-admission), F2-9 (LRU thrash), F2-11 (fragmentation), F2-19 (no invalidation = compliance) → MED to HIGH.

**Panel-wide gaps distinct from v2 (7) and v3 (6):**
1. **Hit-ratio simulator is the gate, not the verdict** — both Deep and Fresh assert ranges 40–75% without simulation. One-week replay of CF access logs against a sized LRU/LFU sim is the actual gate. **HIGH.**
2. **Browser cache as L1 quantification** — at 91% edge hit, marginal user load on edge is 9% of total; lifting browser-cache hit ratio from ~40% to ~80% via immutable URLs cuts edge load ~67% → CDN egress drops proportionally. **Plausibly hits 30% CFO target alone, no infra change.** HIGH.
3. **Workload stratification** — 60% UGC long-tail vs 40% catalog (predictable, pre-warmable). Panel treats 8M as homogeneous; Origin Shield + selective pre-warm + cheap CDN for tail is a stratified architecture nobody priced. HIGH.
4. **`Save-Data` + Client Hints (`Sec-CH-DPR`, viewport-width)** — responsive image delivery cuts bytes 20–40%; CF Functions does this out of box. MEDIUM.
5. **NLB / connection limits** — fronting tier needs to handle ~10s of millions concurrent TLS connections; per-NLB connection-table limits + AWS pre-warm requests not in plan. MEDIUM.
6. **Redis 2024 RSAL/SSPL license risk** — non-zero forward risk for a "we'll own this for 10 years" pitch (Valkey/MemoryDB switch cost). LOW–MEDIUM.
7. **Hot-key / hot-shard concentration on viral content** — single shard NIC saturates while others idle; CDN absorbs naturally. Mitigation requires read-replica fan-out + client LB not scoped. HIGH.
8. **"$48K/mo" baseline unverified** — invoice vs list-price model; actual savings target may already be partly captured by an existing private pricing agreement. MEDIUM.
9. **Promotion-as-architecture-portfolio** — recently-promoted principal pitching principal-sized rewrite is structural, beyond just CoI; tie proposal to written success criteria (cost ≤ $33.6K, p99 latency, hit ratio ≥ 91%) before commit. HIGH meta.
10. **Reverse off-ramp not specified** — migrating *back* to CloudFront after a year is a second migration with its own risk; large decisions should specify reversal cost up front. MEDIUM.

**Cumulative panel-wide gaps across v2+v3+v4 = ~23** distinct levers above the 4-reviewer panel.

**Why:** Three 5th-Fresh passes on the same material continue to surface mostly non-overlapping levers — the gap-discovery process is stochastic. The strongest cumulative addition: **edge-to-user egress is the cost driver, not the cache layer (v3-N2) + browser-cache hit-ratio elevation via immutable URLs likely meets 30% target alone (v4-2).** These two together name the cheapest 30% lever the panel under-emphasized.

**How to apply:** When consolidating Redis-as-CDN final verdict, merge v2 (7) + v3 (6) + v4 (10) panel gaps for 23 additions. Block on: (a) hit-ratio simulator, (b) decomposed $48K bill, (c) AVIF + immutable URLs experiment, before Redis path is re-evaluated.
