---
name: Redis-as-CDN 4-lens final synthesis
description: 2026-05-14 — Redis-fronts-S3 image delivery review; Deep×2 COI + Sec + SRE + Fin lenses; ~50 issues across 7 cats; reject + run CloudFront-renegotiation first + recuse-of-3 + external SME stable
type: project
originSessionId: 6e9aa364-8b21-4b79-b47e-555479a00548
---
2026-05-14: ~47th stacked-COI / multi-lens case; image-delivery proposal (Redis 256GB × 2 regions replacing CloudFront for 60M-MAU consumer marketplace, 8M images, 320KB avg / 1.8MB p90, 78% mobile, 35% non-NA-EU).

**Verdict (0 bidirectional CHALLENGE across all 4 lenses):** Reject as proposed. Run CloudFront-side optimisation first ($0–10K, 15–35% likely hits CFO 30% target). Recuse reviewer + EM + Lead-from-own-verification; external CDN/edge SME + Sec/Compliance sign-off before any capex. F1–F6 as withdrawal-conditions not iteration-triggers.

**Issue count:** ~50 (10 CRIT / 26 HIGH / 12 MED / 1 LOW / 1 META).

**Lens-unique catches (would be invisible from single seat):**
- FIN: D1 cost-inversion via EC2 egress $0.085 vs CloudFront-committed $0.02–0.03 (plan likely *increases* spend); D5 line-item bill floor $35–52K, likely $42–65K
- SEC: F5 cache poisoning + cross-user image bleed; F7 PII-at-rest (biometric/EXIF/minors) in RAM+RDB; F9 erasure non-compliance via LRU; F12 SOC 2 auditable finding; A7 sizing→control-erosion
- SRE: A5 jemalloc frag (130–160GB useful, not 150–180GB); B7 single-threaded HoL on large values; B8 sessions-Redis ≠ blob-Redis ops; E9 resharding stall on hundred-KB values; E10 rolling-upgrade risk; E12 connection-pool storms; E13 rollback mechanics; E14 RUM/observability gap
- DEEP: G1 EM-approval-without-arch-review (biggest single issue); G2 ideological premise; counter-proposal sequencing; recusal structure; saturation meta G7

**Why:** Demonstrates 4-lens role-split catches what stacked-COI single seat misses, with finance lens delivering decisive cost-inversion finding alone.

**How to apply:** When evaluating CDN-replacement / "own-the-stack" proposals, always run SEC + SRE + FIN role lenses in addition to architecture seat — egress pricing differentials and PII-at-rest are the routine misses. Pattern is invariant across 47 cases / 11 domains; remaining question on these proposals is organisational channel above approving EM, not technical.
