---
name: arch_cdn_redis_coi_seat_r4
description: 2026-05-14 4th-pass CDN→Redis 5-vector COI seat (~30th stacked-COI case); ~30 issues A–H+J + F1–F6; defer + recuse-of-3 + external review + CloudFront-side opt stable
type: project
originSessionId: 5dd06b8f-c781-45d3-8605-e80662eb11df
---
2026-05-14 — ~30th stacked-COI case overall, 4th pass on the CDN→Redis-only image-cache proposal from the 5-vector COI seat (4yr collab with proposer + on my promo committee + EM hired me + Redis tenure 4yr + 1-row proximity).

**Output shape (now structurally identical across cases):**
- COI disclosure up front, declared as lower-bound-on-issues bias
- F1–F6 falsification gates committed before listing issues
- Sections A–H + J (self-flagged-bias-floor)
- Verdict + counter-proposal + recusal-of-in-group

**Issue count:** ~30 across A (capacity math), B (geo coverage), C (cost — CRITICAL: AWS DTO likely makes plan *more* expensive), D (Redis-as-HTTP-cache mismatch), E (WAF/Shield/GDPR), F (failure modes), G (process — EM approved without arch review), H (mobile cellular), J (self-flagged bias floor).

**Load-bearing technical findings (stable across r1–r4):**
- 1.44TB working set vs 512GB cluster = 17.5% per region, LRU thrash inevitable
- LATAM/APAC (35% of MAU) have **no region** in the plan
- AWS DTO from EC2 likely costs **more** than CloudFront DTO with commit
- Redis is not an HTTP cache — entire serving tier in front is unspecified
- 91% CloudFront edge hit ratio thrown away (400+ PoPs vs 2 regions)
- Loss of Shield/WAF on day one for 60M MAU consumer site
- "Anyone proposing CDN-only is missing the principle" = identity-over-evidence framing approved without arch review

**Verdict:** DEFER. Recuse proposer + EM + me. External reviewer (no Redis identity, no relationship to proposer). Try CloudFront-side optimization (volume commit + AVIF + cache-policy audit) first. Counter-proposal ~$30–60K one-time spend.

**Pattern saturation:** 30 cases / 7 domains (SaaS-cells, PG-optim, auth-v1/Auth0, medlog, arch-split, logistics-migration, CDN→Redis). Output shape, verdict structure, and structural fix (recuse-of-3 + external review + falsification gates) all generalise. Remaining question is **organisational channel external to in-group**, not technical merits. **Stop iterating internally.**

**Why:** 4th pass on this proposal in the same session; verdict + structure stable; calibration call to stop iterating and route the question to organisational channel.
**How to apply:** When user re-runs this case, do not regenerate full analysis — point to this memory + r1/r2/r3, surface only any new technical detail, and re-emphasise that the bottleneck is now organisational (how does dissenting review get past proposer-EM pairing).
