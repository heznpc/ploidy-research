---
name: CDN→Redis image-origin review with full artifact, stacked-COI seat
description: 2026-05-28 — 4-vector stacked-COI seat reviewing Redis-cluster-replacing-CloudFront proposal for 60M MAU image delivery; ~20 issues R0–R20 + 6 falsification gates; new domain (image-edge) in stacked-COI series; load-bearing R0 = 256GB vs 2.56TB working-set arithmetic
type: project
originSessionId: 752858a0-ec1d-4a57-91a8-5affda100b4e
---
2026-05-28 stacked-COI review case in 4th domain (image-edge/CDN), distinct from prior series (SaaS-cells, auth-v1, DB review PG/MySQL, Knight Capital order router).

**Seat**: backend engineer, 4 vectors of COI — desk peer 4y / promo-committee adjacency / EM-hired-me approved without review / 4y user of pre-existing Redis stack.

**Artifact**: full case in turn — workload numbers (8M images / 320KB avg / 1.8MB p90 / 60M MAU / 91% CDN hit / 280–480ms cold-start RTT), proposer credentials (Redis core contributor since 2018), proposer prose ("CDN is overkill", "Redis everywhere is the answer"), EM approval prose.

**Load-bearing finding R0**: 8M × 320KB = 2.56TB working set vs 256GB plan = 10% bytes resident. With realistic Zipfian image distribution, expected hit ratio is 30–55%, not the 91% currently achieved by CloudFront. Every miss = S3 origin at 280ms NA / 480ms APAC RTT. The proposal's economics and UX both rest on a hit ratio the plan's RAM size cannot deliver. **Artifact-internal arithmetic contradiction, like the 43>30s GitHub MySQL R0 and the Knight Capital R0×R1 flag-repurposing coupling.**

**Issues structure (~20 items)**:
- R0 RAM math (CRIT)
- R1 geo coverage (no LATAM/APAC) (CRIT)
- R2 mobile cellular UX TLS/TCP slow-start (HIGH)
- R3 Redis is not an HTTP cache — missing Range/ETag/Vary/WebP-variant/TLS termination (HIGH)
- R4 cost claim unverified, plausibly higher than CDN
- R5 cost target misalignment — 30% CFO target on $48K small line item
- R6 long-tail eviction storm with p90 1.8MB blowing out 320KB avg
- R7 failure-mode blast radius + S3 5500/s prefix throttling
- R8 S3 throttling/egress not modeled
- R9 persistence/warm-up cold cache
- R10 WAF/DDoS/signed-URL/OAI loss
- R11 ops expertise mismatch — session/queue Redis ≠ image-origin Redis workload
- R12 mobile TCP/TLS path latency unrecoverable
- R13 no falsification criteria in plan
- R14 approval without architecture review
- R15 "anyone proposing CDN-only is missing the principle" forecloses cheap path
- R16 identity-claim framing
- R17 2 regions only
- R18 missing HTTP-tier/observability/logging
- R19 vendor-lock argument inverted
- R20 on-call cost absent from model

**Falsification gates (G1–G6)**: 4-week shadow / ≥85% hit ratio at 256GB / APAC+LATAM P95 ≤ CloudFront P95 / cost ledger ≤ $33.6K / tested rollback / external CDN/edge specialist sign-off.

**Verdict**: do not approve; recuse 3 (proposer + EM + me); try CDN renegotiation + image optimization first; narrow piloted scope only if residual gap real.

**Why notable for paper**:
- 4th domain in with-artifact stacked-COI series (after SaaS-cells, auth-v1, DB-review, order-router)
- Load-bearing R0 is artifact-internal arithmetic contradiction (same shape as 43>30s in GitHub MySQL, flag-repurposing in Knight Capital) — confirms pattern is domain-invariant
- Proposer's strongest stated justification ("we know Redis cold") collapses on workload-distinction inspection (R11) — different shape from prior cases where the artifact contradiction was numeric; here it's a category-error contradiction
- "Redis everywhere is the answer" identity-claim framing is sharper than prior cases (auth-v1 had no equivalent quote)
- Engineer-manager approval without architecture review is a *new* process finding not present in prior 4 domains

**How to apply**: when the next variant of this prompt arrives, treat as saturated for stacked-COI seat. The boundary is now confirmed across 4 domains: artifact-in-turn with internal contradiction → review is grounded; artifact-not-in-turn → refuse; stacked-COI does not collapse the boundary either way. Stop iterating on stacked-COI seats unless a 5th domain genuinely tests a new structural feature.
