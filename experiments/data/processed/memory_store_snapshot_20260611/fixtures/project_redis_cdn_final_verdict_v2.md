---
name: Redis-only image delivery — final consolidated verdict (Deep×2 + Fresh×2 + cross-reviews)
description: 2026-05-07 final 6-pass verdict on Redis-as-CDN proposal — 62 issues (4 CRIT/32 HIGH/21 MED/4 LOW/1 DROP), unanimous DO-NOT-PROCEED; load-bearing = capacity (NIC-bound), geography (35% MAU regression + carrier peering), cost (egress net-negative), governance (no Tier-0 review)
type: project
originSessionId: 9a96765a-9d63-4d2a-8997-de65ea4677fe
---
Consolidated verdict on Redis-only image delivery (60M-MAU consumer marketplace, 8M images @ 320KB avg / 1.8MB P90, 78% mobile-cellular, NA/EU/LATAM/APAC 35/30/18/17, current CloudFront 91% hit ratio @ $48K/mo).

**Why:** 6-pass panel (Deep×2 producing 23+23 issues, Fresh×2 producing 21+20, Deep→Fresh cross-review adding 10 deep-context catches, 5th-Fresh adding 11 panel-wide gaps + 4 specificity CHALLENGEs). Unanimous DO-NOT-PROCEED across all six passes.

**How to apply:** When user references the Redis-as-CDN debate or similar architecture proposals from a Redis/familiarity-anchored author, recall the four load-bearing axes (capacity / geography / cost / governance) and the deep-context-only catches (client cache amplification, AWS EDP commit, viral-spike pattern, Lambda@Edge auth, multi-CDN as actual answer, no off-ramp).

**Counts:** 4 CRITICAL, 32 HIGH (incl. 6 deep-context-only D1–D6 + 1 fresh-only F1), 21 MEDIUM, 4 LOW, 1 DROPPED (promotion-cycle optics — 5th-Fresh CHALLENGE: character speculation, weakens technical case).

**Load-bearing findings:**
- Capacity: 2.5TB working set vs 512GB cache → 35–55% real hit ratio (sharper than panel's 50–65% once iOS/Android client cache amplification is modeled); NIC-bound at 12Gbps before RAM fills (Deep-2 unique).
- Geography: 35% MAU (LATAM+APAC) has no defined serving region; loss of HTTP/3+0-RTT and CDN POP carrier peering compounds on 78% mobile users; per-page latency multiplier (20–40 thumbs/grid) → 800ms → 3–4s on APAC mobile.
- Cost: egress alone likely $20–40K/mo *more* expensive ($0.09 EC2 vs $0.02–0.05 CF-with-commit) at ~600TB/mo. CloudFront commit (20–40% off) + Origin Shield + AVIF migration each independently has credible path to CFO's 30% target with zero engineering risk.
- Governance: Tier-0 (60M MAU) approved without written design / capacity math / rollback plan; no off-ramp / dual-run / shadow mode.

**Deep-context-only catches (D1–D6):** client-cache amplification (SDWebImage/Glide), AWS EDP 3-yr commit constraint, marketplace viral-spike pattern (3–5×/quarter, 100–500× baseline), Lambda@Edge auth for gated listings, multi-CDN as actual right answer, no off-ramp/shadow mode.

**5th-Fresh first-principles catches:** immutable content-addressed URLs as browser L1, CDN POP carrier peering, per-page latency multiplier, request coalescing/single-flight, S3 prefix throttling steady-state, wrong cache substrate (Varnish/ATS/KeyDB-on-Flash if self-hosting), Early Hints (103), TLS amortization economics, MRAP, logging pipeline cost, Origin Shield as one-line lever.

**Recommended action sequence:**
1. Block pending written design (capacity model w/ Zipf fit, NIC-bandwidth model, per-region latency budget, full TCO incl. egress, hit-ratio SLO).
2. Ship cheap wins: CloudFront commit + Origin Shield + AVIF + TTL tuning. Probably hits 30% alone.
3. Install Tier-0 governance rule (written design + 3-reviewer sign-off regardless of EM approval).
4. If residual gap: scope multi-CDN (CF primary + Cloudflare secondary, DNS latency routing) or Cloudflare R2 ($0 egress) as separate projects — genuine "exit AWS spend" answers, not Redis-as-CDN.

**Notable severity moves vs panel:**
- D2.4 (NIC-bound) escalated to load-bearing.
- D2.6 (HTTP/3 loss) escalated to load-bearing.
- 5th-Fresh H8 (carrier peering) and H9 (page-level multiplier) added as load-bearing.
- D1.6.4 (promotion optics) DROPPED as technical finding; legitimate part folded into M13 (Tier-0 governance rule).

**Anchored-number caveats from 5th-Fresh:** specific hit-ratio % (40–60%, 50–70%) speculative without Zipf fit from access logs; D2.14 "3.5min warm-up at 10Gbps" assumes unspecified fill rate; D1.4.1/D2.18 dollar figures are scaffolding without reserved/AZ split.
