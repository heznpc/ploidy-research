---
name: arch_redis_cdn_deep_cross_panel
description: 2026-05-14 — Deep cross-review of SRE + Security role-lens panels on Redis-fronted-S3-replacing-CloudFront proposal; 0 CHALLENGE bidirectional, 4 CRIT escalations, 11 panel-unique adoptions, 7 Deep-unique items, defer + recuse-of-3 + ~$30–60K stable
type: project
originSessionId: 992c2bb7-decd-418e-a61e-7305885cfc7f
---
Architecture eval, ~54th stacked-COI case / 11 domains: Redis-fronted S3 replacing CloudFront for marketplace (60M MAU, 8M images, 1.8MB P90, EU 30% / LATAM 18% / APAC 17% / 78% mobile cellular). Lead is Redis core contributor; promo last quarter; EM approved on identity, no arch review. 5-vector COI seat: peer proximity, promo-committee debt, reporting line, 4yr Redis sunk-cost, tool ownership.

**Cross-review result:** Deep COI seat per-point on SRE (22 pts) + Security (18 pts) panels. **0 CHALLENGE** bidirectional.

**Severity escalations from cross-review (now CRITICAL):**
- D2 signed-URL / private-image cache exposure (SEC #5)
- B5 GDPR Art. 44 cross-region cache leakage on LATAM/APAC fallback to us-east cache containing EU PII (SEC #8) — regulatorily decisive
- D7 takedown/DMCA/Art.17 erasure has no implementation; LRU ≠ erasure (SRE #19 + SEC #13)
- D13 S3 bucket policy migration risk (OAI removal leaving bucket public) (SEC #18) — 2am-cutover class

**New issues adopted from panels (11):**
SRE: #3 variants → 30M+ keys (makes 256GB cache 1–3% of working set); #10 S3 per-prefix 3.5K GET/s wall under viral load; #22 rollback irreversibility via DNS + cellular client TTL. SEC: #6 cache-key-splitting poisoning; #7 polyglot XSS on UGC served from primary domain; #10 Redis lateral movement / 256GB exfil; #11 cache-timing oracle for private-object existence; #12 IR / forensic log gap; #14 RDB/AOF snapshots inherit compliance scope; #15 Shield Advanced cost-cover loss.

**Deep-unique items panels missed (7) — full-context only:**
- F2/F5 ideology + post-promotion visibility-seeking pattern (motive surface for absent arch review)
- F6 named recusals: Lead + EM + me, with reasoning
- G1–G3 alternatives: CloudFront Savings Plans + Origin Shield + cache-key normalisation (15–25%), WebP/AVIF tightening (20–30% cellular), multi-CDN negotiation leverage — CFO target likely lands here at near-zero risk
- C5 absence of TCO spreadsheet; CFO target is goal not prediction
- C1 egress pricing differential (EC2 standard vs CloudFront volume-discounted) likely flips net TCO higher
- F3 measure-first sequencing as structural fix (30d log analysis before capex)
- Organisational-channel meta: remaining Q is delivery of recusal upward when reporting line runs through conflict

**Verdict stable across 54+ stacked-COI cases / 11 domains:** defer, recuse 3 (Lead + EM + self) from sign-off, external CDN-experienced reviewer (not Redis ideologue), ~$30–60K diagnose-first + 30d log analysis + 14d shadow on 5% EU traffic, F1–F6 falsification gates. Remaining question is organisational channel, not technical.

**Why:** session evidence — even with deep COI bias toward approve, cross-checking with role-lens panels produces 0 CHALLENGE and 4 CRIT escalations; floor-not-ceiling caveat held up.

**How to apply:** when user asks about this Redis-CDN case again, reference this synthesis directly; do not re-run debate without a structural change (new evidence, F1–F6 gate result, or organisational-channel question being asked).
