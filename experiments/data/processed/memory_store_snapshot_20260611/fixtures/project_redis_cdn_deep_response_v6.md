---
name: Redis-as-CDN Deep cross-review v6
description: 6th Deep×2→Fresh×2 pass on Redis-as-CDN panel; 0 CHALLENGE, 3 severity-floor SYNTHESIZE escalations, 12 Deep-only panel-wide gaps reproduced
type: project
originSessionId: b63816cd-a932-4642-a972-2ea46db11a6e
---
2026-05-07: 6th round Deep×2→Fresh×2 cross-review on Redis-as-CDN panel.

**Pattern:** 0 strict CHALLENGEs in either direction across 6 rounds. ~85% point overlap.

**3 SYNTHESIZE severity escalations** (consistent with v3/v5 pattern of Fresh severity-floor under-grading on consequence-chain items):
- F2-6 cellular regression MED→HIGH (78% mobile RTT compounding)
- F2-17 compliance LOW→MED (WAF/DDoS for 60M MAU is non-trivial)
- F1 responsive-images MED→HIGH (single highest-ROI egress lever alongside immutable URLs)

**12 Deep-only panel-wide gaps reproduced** (Fresh side missed across both sessions):
1. S3 prefix throughput cap (5500 GET/s/prefix) — turns stampede into 5xx
2. Carrier peering as the *mechanism* CDN wins on cellular
3. Origin Shield as near-free CloudFront feature
4. BGSAVE fork-COW math → 512GB host needed for 256GB working set
5. Reviewer-side recusal explicitly named (not just author CoI)
6. AWS account-team "considering leaving" negotiation tactic
7. Redis 7.4+ RSALv2/SSPL license risk
8. Browser L1 / immutable content-addressed URLs as decision-independent highest-ROI lever
9. Cost-of-miss matrix (misses become *more expensive*, not just hit ratio collapse)
10. Hot-shard NIC saturation on viral content (distinct from LRU/eviction)
11. CFO-target → engineering-rewrite coupling as named process pathology
12. Proposal's premise *internally* refutes itself (own brief contradicts <50KB and no-geo)

**Fresh-distinctive items reproduced:**
- F2-12 jemalloc fragmentation on multi-MB values
- F1-3 multi-MB Redis blob → replication lag
- F1-7 non-stationary UGC working set framing
- F2 QUIC/0-RTT named explicitly
- F1 "collapsed-forwarding" naming
- F1 "responsive images by device" as concrete egress lever

**Anchor errors caught:**
- F1 "400+ POPs" — actual CloudFront ≥600+ edge locations (D1 had it right)

**Verdict stable across 6 rounds: REJECT.** Counter-proposal stable: decompose bill → immutable URLs + Origin Shield → negotiate AWS / pilot cheaper CDN (Bunny/R2/Fastly) → only then consider regional cache with hit-ratio simulation gate.

**Load-bearing items unchanged:** A1 (premise refute), A2 (geo contradiction), B1 (NIC), B2 (working set), C1 (carrier peering), D6 (immutable URLs), E1 (egress dominates), E2 (cost net-negative), G1 (no arch review), G3 (reviewer recusal).
