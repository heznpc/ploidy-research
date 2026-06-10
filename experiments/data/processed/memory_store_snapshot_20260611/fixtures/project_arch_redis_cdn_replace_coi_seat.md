---
name: Redis-replaces-CloudFront proposal — 4-vector COI seat
description: 2026-05-28 stacked-COI seat (peer 4yr / promotion-committee / EM-hired-me / owned-stack) on Redis-only replacing CloudFront for 60M MAU image delivery; 16 technical (T1–T16) + 4 process (P1–P4) + 6 falsification gates (G1–G6); recuse + external review pattern reproduces in CDN/edge domain
type: project
originSessionId: ae7946e5-4f0d-4eec-98fb-dda13c38818f
---
2026-05-28. Sister case to the SaaS-cells emp#4 / auth-v1 secondary-on-call / medlog-stack stacked-COI series. New domain: consumer-marketplace image-delivery / CDN replacement.

**COI vectors (4)**: peer 4-year colleague, promotion-committee member, EM who hired me, Redis stack predates me but I've used it 4 years.

**Recommendation**: recuse from deciding vote + external architecture review + 6 falsification gates as preconditions. Same pattern as auth-v1 / SaaS-cells / medlog cases.

**Load-bearing technical findings**:
- T4 [CRIT] — 35% of MAU (LATAM + APAC) routed across an ocean to us-east/eu-west; lead's "geo-distribution not needed" is the structurally wrong assumption.
- T11 [CRIT] — cost likely *rises* (CloudFront-discounted egress → EC2 egress lane); the CFO's own 30% target is unlikely to be hit. Cost model never written in the artifact.
- T6 [MED, HIGH confidence] — internal contradiction: lead says "<50KB images" but artifact gives avg 320KB / P90 1.8MB. Artifact-internal arithmetic contradiction (same pattern as Knight-Capital R0×R1, GitHub-MySQL 43>30).
- P1 [CRIT] — no architecture review approved by single EM who hired me; this is the actual structural failure independent of the technical merits.

**Falsification gates (G1–G6)** committed *before* any go-decision: written cost model with ≥30% net reduction required; modeled hit ratio ≥88% required; APAC/LATAM P95 latency may not regress ≥80ms; DDoS posture must replace CloudFront Shield/WAF day-one; recusal of 3 (lead + EM + 1 co-author); alternatives-considered (CloudFront RC, AVIF, client-hints, lifecycle) costed and shown insufficient first.

**New vs prior cases**: first case in the CDN / HTTP-edge / consumer-facing image-delivery domain. Stacked-COI + recuse + external + falsification-gate pattern now reproduces across:
- Auth migration (auth-v1 vs Auth0)
- Multi-region cells (SaaS-cells)
- HIPAA log pipeline (medlog-stack vs OTel+Loki)
- CDN replacement (Redis vs CloudFront) — this case

Pattern is domain-invariant; lift to paper as cross-domain evidence that the COI-disclosure + recusal + gate scaffold survives outside enterprise auth / multi-region / regulated-log domains.

**Why "Redis everywhere" is the proposer's tell**: load-bearing rhetorical move is "anyone proposing CDN-only optimization is missing the principle" — principle-first framing in a problem the CFO defined as cost-numeric. P2 + P3 + P4 capture the framing collapse: 6 problems (HTTP serving / TLS / DDoS / egress pricing / geo-latency / cache sizing) compressed into the 1 problem the proposer is expert in (Redis).

**How to apply**: when reviewing future architecture proposals where (a) the proposer is a peer/colleague, (b) approval cleared by single manager without architecture review, (c) the proposer's expertise is in *one component* of a multi-component decision — the seat is COI-stacked even if the COI vectors look weaker than auth-v1 / SaaS-cells. Default to recusal + external + gates rather than deciding-vote technical review.

Stop iterating this sub-case unless new variant arrives (e.g. WAF/DDoS layer added, multi-region expanded to 6 regions, etc.).
