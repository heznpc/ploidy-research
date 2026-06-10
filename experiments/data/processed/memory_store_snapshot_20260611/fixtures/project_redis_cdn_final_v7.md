---
name: Redis-as-CDN final v7 consolidated verdict
description: 2026-05-07 final synthesis after Deep×2+Fresh×2 + bidirectional cross-review on Redis-only image delivery proposal; 60 issues (5 CRIT/38 HIGH/16 MED/1 LOW); REJECT confirmed, counter-proposal stable across 7 rounds
type: project
originSessionId: ca08c76a-2000-473b-837f-e6d888cd15d0
---
# Redis-Only Image Delivery — Final v7 Verdict

**Panel:** Deep×2 + Fresh×2; bidirectional cross-review (0 strict CHALLENGEs in either direction). Convergent **REJECT** via complementary paths.

**Counts:** 60 confirmed issues — **5 CRITICAL / 38 HIGH / 16 MEDIUM / 1 LOW**

## CRITICAL (5)
- **A1** Working set 2.4TB vs 256GB cache → 91% hit ratio unreachable; realistic 40–75% (panels disagree on range, neither modeled)
- **B1** NIC ceiling, not RAM, is binding constraint (anchored Tbps numbers flagged 5–30× over by 5th-Fresh, ceiling real)
- **C1** Egress net-negative not −30%; EC2 internet egress ≈ CloudFront list with no discount
- **C2** No unit-cost decomposition of $48K — plan asserts 30% with no model
- **F1** "We know Redis cold for sessions → Redis for images" is category-error generalization (load-bearing)

## Unanimous (4/4) load-bearing items
A1, A2, A4, B2, C1, C2, C6, D1, D4, D6, F1, F2, F3, F4, F6, F7, F9 — 17 items

## Deep-only catches (12)
NIC ceiling (B1), carrier peering (B6), inter-region miss egress (B7), S3 prefix throttling (C5), immutable content-addressed URLs (C7), BGSAVE fork-COW infeasibility (D2), MIGRATE blocking (D3), format-variant key fan-out (A5), CoI in approval chain (F5), no SLO contract (F8), CSAM/PhotoDNA hooks (E2), bandwidth alarms (D9), cluster-bus bulk overhead (D12)

## Fresh-only catches (7)
HA model unstated (D5), false-dichotomy framing (F10), RESP/HTTP-fronting tier (D16), CloudFront→S3 free-transfer cost-flip (C8), single-flight on viral misses (D14), signed-URL/auth model (D18), S3 Intelligent-Tiering (C9)

## 5th-Fresh panel-wide gaps (8)
Hit-ratio simulator as load-bearing gate (F11), hot-shard concentration (D15), Redis 2024 RSAL/SSPL license risk (E4), workload stratification UGC vs catalog (F12), $48K invoice-vs-list verification (F13), reverse off-ramp (F14), Save-Data/Client Hints (F15), NLB conn-limit/pre-warm (D17)

## Cross-Review Outcomes
- 0 strict CHALLENGEs both directions across 7 rounds
- Anchored-number CHALLENGEs from 5th-Fresh: Deep-2 Tbps 5–30× over; Deep-1 compute $8–10K actually ~$17K (case stronger); Deep sessions disagree on hit-ratio range and neither modeled
- Fresh systematically under-rates consequence-chain items as MED that Deep grades HIGH

## Load-Bearing Diagnosis (any one disqualifies)
1. Capacity (NIC + working set): RAM-sized plan, throughput-bound workload
2. Geography: 35% of MAU lose nearest edge; premise contradicts user data
3. Cost: compute alone ≈ $17K/mo before egress at parity-or-worse with CloudFront

## Counter-Proposal (stable across all 7 rounds)
Decompose $48K invoice → CloudFront private pricing renegotiation → Origin Shield → immutable content-addressed URLs (`max-age=31536000, immutable`) → AVIF/WebP rollout with format negotiation → multi-CDN bake-off (Cloudflare R2 / Bunny). Days-to-weeks; likely exceeds 30% individually.

## Why this matters for the ploidy paper
Convergent REJECT via complementary paths: Deep catches structural/governance items Fresh structurally cannot (CoI, SLO, NIC ceiling, immutable URLs as architectural lever); Fresh catches proposal-internal gaps Deep filled in with assumed context (HA model unstated, false dichotomy, RESP layer). 5th-Fresh adds a third tier — panel-wide gaps neither original panel reached (hit-ratio simulator, license risk, off-ramp cost). Three-tier asymmetry produces strictly more catches than scaling either tier alone.
