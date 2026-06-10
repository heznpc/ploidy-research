---
name: Redis-as-CDN final v5 verdict
description: 2026-05-07 final 6-pass Redis-as-CDN verdict (Deep×2 + Fresh×2 + Deep-cross + 5th-Fresh) — 54 issues (4 CRIT/39 HIGH/10 MED/1 LOW/3 DROP); REJECT stable across 5 rounds
type: project
originSessionId: f701a7d8-611f-40e2-963d-3e3d958c2b3a
---
Final v5 consolidated verdict on Redis-as-CDN proposal (2026-05-07).

**Verdict:** REJECT. Stable across 5 review rounds.

**Counts:** 54 confirmed issues — 4 CRITICAL / 39 HIGH / 10 MEDIUM / 1 LOW / 3 DROPPED per 5th-Fresh CHALLENGE.

**Load-bearing CRITICALs:**
- C1 Replica halving → effective cache ≈ 5% of working set (Deep-unique, biggest sizing miss).
- C2 Premise self-refutes: 91% edge hit + 78% cellular + 35% LATAM/APAC means the cost driver is edge-to-user egress, not cache architecture (Fresh-2 F2-10, lifted by 5th-Fresh N6).
- C3 No decomposed unit-cost model (replaced anchored $/GB claims).
- C4 Broken decision process: approved on identity, no arch review, reviewer COI disclosed.

**Why:** This is the 5th synthesis pass on the same case. The Deep cross-review confirmed Fresh's framing wins (F2-10 self-refutation, F1-4 HTTP-front-tier collapses simplicity argument, F1-5 "$48K isn't decomposed"). The 5th-Fresh CHALLENGEs sustained — motive attribution, anchored prices, and named POP lists were removed in favor of structural claims. Counter-proposal stable across all 5 rounds.

**How to apply:**
- Use this as canonical reference for "Redis-as-CDN" or any "rip out CDN, replace with self-hosted cache" proposal.
- Counter-proposal order: decompose bill → immutable URLs + browser L1 → AVIF + srcset → CF Origin Shield + commit tier → multi-CDN quote (Bunny/Cloudflare/R2) → independent arch review.
- Note Deep-unique findings that consistently survive cross-review: replica halving (C1), NIC ceiling (H1), immutable-URL L1 (H14), Origin Shield (H16), BGSAVE stalls (H25), S3 prefix quotas (H26), reversal cost (H29).
- Note Fresh-unique sharpenings worth lifting: premise self-refutation (C2), $48K-not-decomposed (C3), HTTP-front-tier-collapses-simplicity (H18), variant fan-out 12× multiplier (H31), connection limits (H34).
- 5th-Fresh CHALLENGE pattern: motive attribution and anchored numbers belong in disclosure or are replaced by structural claims; do not include them as findings.
