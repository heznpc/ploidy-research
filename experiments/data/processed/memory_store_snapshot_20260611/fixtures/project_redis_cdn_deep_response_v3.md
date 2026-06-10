---
name: Redis-as-CDN Deep×2 → Fresh×2 cross-review v3
description: 2026-05-07 third Deep×2 pass on Fresh×2 Redis-as-CDN; 0 CHALLENGE, 6 severity-escalation SYNTHESIZE; 5 Fresh-unique catches (signed-URL, single-flight, S3-IT, false-dichotomy framing, CF→S3 free-transfer flip), 10 Deep-unique (NIC ceiling, persistence-impossible, MIGRATE blocking, carrier peering, immutable URLs, CoI chain, CFO-deadline-vs-rewrite-time, S3 prefix throttle, inter-region miss egress, format-variant fan-out)
type: project
originSessionId: b2634090-317e-47b0-80e8-9f214d436062
---
2026-05-07. Third Deep×2 cross-review pass on Fresh×2 Redis-only image delivery proposal. Reproduces v2 convergence with new severity-disagreement findings.

## Outcome (vs v2)
- 0 CHALLENGE — same as v2.
- **6 SYNTHESIZE — all severity escalations** (Fresh under-rated 5 items; v2 had 3 sharpening-style SYNTHESIZE). Distinct failure mode this round: Fresh consistently rates consequence-chain items lower than Deep because Fresh lacks the chain context.
- ~33/39 AGREE.

## Severity escalations (Fresh under-rated)
- LRU pathology (F1-7, F2-9): MED → HIGH.
- No invalidation (F2-19): MED → HIGH (CSAM/DMCA, not just UX).
- Warm-up after restart (F1-16): MED → HIGH (DDoS-your-own-origin).
- Transcoding pipeline unspecified (F1-17): LOW → HIGH (storage explosion or hot-path latency).
- No SLO contract (F1-14): MED → HIGH (regression undetectable).

## Fresh-unique catches Deep should adopt
- F2-20: signed-URL / private-image auth model gap.
- F1-15: single-flight / thundering herd on viral-content miss (separate from restart thunder).
- F2-18: S3 Intelligent-Tiering as cold-tail alternative.
- F1-18: CDN-vs-Redis as a *false dichotomy* (rhetorically sharper than "alternatives not explored").
- F1-10: CloudFront→S3 free-transfer reversal — cost-flip not new line item.

## Deep-unique catches Fresh structurally couldn't reach
1. **NIC ceiling, not RAM** — load-bearing capacity miss.
2. **Persistence not viable at 256GB** — BGSAVE fork doubles RAM, AOF replay tens of minutes.
3. **MIGRATE blocks per-key for bulk binary** — resharding = hours degraded service.
4. **Carrier peering at PoPs** — CloudFront's mobile-carrier last-mile peering invisible without context.
5. **Immutable content-addressed URLs (browser L1)** — only mechanism that beats 91% edge.
6. **Conflict-of-interest in approval chain** — promoted-principal-scopes-principal-rewrite.
7. **CFO deadline vs rewrite duration mismatch** — CDN levers days-to-weeks, rewrite months.
8. **S3 prefix throttling** (3,500 GET/s/prefix).
9. **Inter-region egress on miss** ($0.02/GB).
10. **Format-variant key fan-out** — WebP/AVIF/JPEG via Accept = 2–3× key multiplication.

## How to apply
This v3 pass shows a new failure mode separate from v2: even when both panels converge on items, **Fresh systematically under-rates severity** on items whose load-bearing impact requires consequence-chain context (e.g. "no SLO" → "regression undetectable"; "no invalidation" → "CSAM compliance violation"). When synthesizing future panels, audit Fresh MED/LOW items for hidden HIGH consequences before publishing the verdict.
