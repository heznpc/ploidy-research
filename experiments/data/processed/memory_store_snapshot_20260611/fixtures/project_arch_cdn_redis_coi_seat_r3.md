---
name: arch CDN→Redis COI seat r3 (~29th stacked-COI case)
description: 2026-05-14 3rd-pass CDN→Redis image-cache 5-vector COI seat; ~30 issues A–J + F1–F6; defer + CloudFront-side opt + recuse-of-3 + external CDN/SRE review stable; pattern saturated across 29 cases / 7 domains
type: project
originSessionId: e7f2b239-514a-4061-833a-a0b68e97e9bc
---
2026-05-14: 3rd-pass eval of CloudFront→Redis-only image cache from 5-vector COI seat (peer-of-Lead + promo-committee + EM-hired-me + Redis-stack-predates-me + same-row identity).

**Falsification gates committed up front:** F1 cache-fits-in-256GB, F2 APAC/LATAM no regression, F3 ≤$33.6K/mo all-in, F4 origin GETs not up, F5 mobile P95 not up, F6 no GDPR/LGPD expansion.

**Issues A–J:**
- A: cache-size math wrong by 5× (2.56TB working set vs 512GB total) — F1 fails on its own numbers
- B: APAC + LATAM = 35% MAU lose edge entirely, +300–400ms cellular — F2 fails
- C: 91% edge hit ratio is the asset being discarded; egress flips from CloudFront-tiered to our NAT/IGW
- D: Redis wrong DS for 320KB–1.8MB blobs; single-threaded I/O, proto-max-bulk-len, conn pool > RAM as limit
- E: CloudFront-side opt (Origin Shield + tiered + TTL + AWS private pricing) never costed; ~25–35% plausible at $1–3K/mo
- F: blast radius grows — Redis down = S3 thundering herd; cold-restart eviction storm; no replication topology specified
- G: new tier-1 service ownership; 6yr Redis-ops experience is on session+queue, not large-blob CDN replacement
- H: lost edge capabilities (TLS term, WAF/Shield, signed URLs, image transform, H3/QUIC)
- I: GDPR + LGPD processing footprint expands
- J: EM waived arch review on identity grounds; "we know it cold" is sunk-cost not technical; Lead's rhetorical pre-emption of CloudFront-opt alternative; no falsification/rollback in proposal

**Verdict:** Defer. Counter-proposal: CloudFront-side opt first (~3–6wk zero-arch-risk), external CDN/SRE consultant ($10–20K), recuse Lead+EM+self from final call.

**Pattern note:** 29th stacked-COI case / 7 domains (SaaS cells, PG optim, arch split, medlog, auth-v1, logistics-migration, CDN→Redis). Output structurally identical across cases — defer + diagnose-first + recuse-of-3 + external review + cheaper alternative. Remaining question is organisational (how does CFO mandate get honest technical answer when proposer + EM + only reviewer are all in-group?), not technical. Stop iterating on technical merits.
