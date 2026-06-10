---
name: arch redis-CDN SEC+SRE panel per-point on Deep×2 (round 3)
description: 2026-05-14 ~60th stacked-COI case — SEC+SRE panel per-point on Deep×2 Redis-image-CDN; 0 CHALLENGE bidirectional; 12 panel-unique adds; 5 severity escalations to CRITICAL on plan-as-written (D2 signed-URL/per-object ACL, D1 WAF/DDoS, B1+GDPR Art. 44 cross-region fallback, D6 cold-start stampede, D10 S3 bucket migration); defer + recuse-of-3 + 3-headed external review + $30–60K diagnostic stable
type: project
originSessionId: 05ee2f83-971f-413e-aed0-cf64f7839745
---
# Redis Image CDN — SEC+SRE Panel Per-Point on Deep×2 (round 3)

**Date:** 2026-05-14
**Case:** ~60th stacked-COI case / 11th distinct domain (image-CDN), 3rd pass on this domain (prior: v1 8-unique, v2 11-unique panel-unique with FIN; this round SEC+SRE-only with severity-escalation lens)

## Process

- Panel = SEC auditor + senior SRE on incident-call (no FIN in this round's role-lens panel)
- Input: Deep×2 (5-vector COI seat with F1–F6 gates and A–G taxonomy) + Fresh-alt SEC + Fresh-alt SRE single-seat reviews
- 0 CHALLENGE bidirectional across panel vs Deep
- ~85% issue overlap; panel adds role-specific specifics + severity-floor lift

## Severity Escalations to CRITICAL on Plan-as-Written

| Issue | Deep severity | Panel | Reason |
|---|---|---|---|
| D2 signed URL / per-object ACL | HIGH | **CRITICAL** | Single most likely breach mechanism — UGC marketplace certainly has access-controlled content; cache key collision = world-readable leakage |
| D1 WAF / bot / DDoS | HIGH | **CRITICAL** | Direct-to-EC2 exposure of image plane for 60M MAU is known-bad |
| B1 + GDPR Art. 44 cross-region fallback | HIGH UX / unflagged compliance | **CRITICAL compliance + HIGH UX** | Plan silent on EU routing → defaults to "any region serves any user" |
| D6 cold-start stampede | HIGH | **CRITICAL** | First post-restart incident; S3 per-prefix 3,500 GET/s throttles under stampede |
| D10 S3 bucket policy migration | not flagged by Deep | **HIGH one-time** | If OAI removed without locking proxy egress identity → bucket world-readable |

## Panel-Unique Adds (12, beyond Deep A–G)

- **D7 [SEC HIGH]** Cache poisoning — UGC paths as cache keys, key-splitting attacks
- **D8 [SEC HIGH on marketplace domain]** MIME-sniffing / polyglot XSS if `X-Content-Type-Options` regresses
- **D9 [SEC MED]** Timing side-channel — hit-vs-miss latency leaks private-object presence
- **D10 [SEC HIGH one-time]** S3 bucket policy migration leak risk
- **D11 [SEC MED]** Snapshot-as-PII — RDB/AOF brings user images under same compliance regime
- **D12 [SRE HIGH]** No invalidation API for DMCA / NCMEC / GDPR Art. 17 erasure across cluster
- **E6 [SRE MED]** RDB fork() CoW cost on 256GB under write load
- **E7 [SRE MED]** Single-AZ vs multi-AZ topology unspecified
- **G6 [SRE]** CloudFront Origin Shield alone often raises hit ratio 2–5pp on long-tail UGC at near-zero cost — test before redesign
- **F1-add [SRE]** Variant key multiplier — 30M+ keys not 8M after WebP×DPR×sizes
- **F1-add [SRE]** Byte-hit ratio required, not request-hit (1.8MB P90 means request-hit can be high while bytes still go to origin)
- **F2-add [SEC+SRE]** TLS-handshake P75 separate metric; P95/P99 not P75 (image-grid pages fan out, tail dominates LCP)

## Falsification Gate Hardening (Panel → Deep's F1–F6)

- **F3-finance** baseline must use CloudFront committed-use / Savings Plan pricing, not on-demand list, else comparison is rigged
- **F4 expanded** must include cache-key normalisation + MIME-sniffing + invalidation API + threat model — not just WAF/signed-URL/transformation
- **F5 expanded** shadow test must include (a) cold-restart stampede test, (b) eviction-storm test under viral-upload burst, (c) S3 per-prefix throttle headroom check, (d) timing-oracle measurement
- **F6 strengthen** external review = 3-headed (CDN senior + security architect + SRE), not single CDN engineer

## Verdict (stable across panel + Deep)

Same as Deep + 4 additions:
1. External review must be 3-headed (sec + SRE + CDN)
2. F4 capability-gap closure must be funded + timed *before* cutover, not measured after
3. Finance baseline must use CF committed-use, not on-demand list
4. GDPR routing policy explicit before any EU shadow test

**Remaining Q organisational, not technical** — consistent with saturated pattern across ~60 stacked-COI cases / 11 domains.

## Pattern Notes

- First per-point cross-check that flags **S3 bucket migration leak (D10)** as a distinct one-time risk Deep missed.
- Panel lens consistently lifts security/compliance items from HIGH → CRITICAL on plan-as-written (5 items this round) without inventing new categories — same finding seen severely.
- 0 bidirectional CHALLENGE 60+ cases.
- Saturated.
