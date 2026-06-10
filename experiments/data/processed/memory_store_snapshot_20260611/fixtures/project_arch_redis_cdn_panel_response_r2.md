---
name: Redis-as-CDN panel (SEC+SRE+FIN) response to Deep×2 COI seat — round 2
description: 2026-05-14 ~60th stacked-COI case / 11 domains — 2nd SEC+SRE+FIN panel per-point on Deep×2 5-vector COI Redis-fronting-CDN; 0 bidirectional CHALLENGE; 5 severity escalations (A5/D6/C1 → CRITICAL, E1/E2 → HIGH); 7 panel-unique (UGC/CSAM CRIT, GDPR Art.17, audit-log gap, cache poisoning, implicit CF features inventory, compliance chain, key-naming); F1/F2/F3 numerical tightenings; defer + recuse-of-3 + F4-first + external-review + organisational-channel stable; saturated
type: project
originSessionId: 243dc903-3a3c-4b20-b390-3c0dc0d19caf
---
# Redis-as-CDN — 2nd panel (SEC+SRE+FIN) response to Deep×2 5-vector COI seat

**Date:** 2026-05-14
**Case index:** ~60th stacked-COI case across 11 domains (Redis-CDN now 2 passes).
**Panel:** Security auditor (Fresh-alt S1) + Senior SRE on-call (Fresh-alt S2); FIN lens applied to TCO claims.
**Panel COI:** none with author / EM / Lead / Deep reviewer.
**Relation to prior pass:** Independent panel pass; converges with `project_arch_redis_cdn_panel_response.md` (r1) — defer + recuse + F4-first + external-review remain stable.

## Convergence

- **Bidirectional CHALLENGE: 0** across 30 Deep points + 6 falsification gates + recommendation.
- **AGREE: 30/30** (with severity floor on 5 items).
- **Panel-unique findings: 7** (UGC/CSAM CRITICAL is highest-severity panel-unique).
- **SRE/FIN sharper numbers vs Deep:** F1 ≤150GB usable (vs 200GB nominal), F2 ≤+25ms (vs +50ms), C1 plausibly **2× current bill** (vs 0.7× target).

## Severity escalations panel applies

| Deep ref | Deep sev | Panel sev | Reason |
|---|---|---|---|
| A5 (35% MAU loses edge) | HIGH | CRITICAL | Product-harm latency regression on growth segments |
| D6 (no DDoS/WAF equivalent) | HIGH | CRITICAL | Day-1 exposed surface, no equivalent control |
| C1 (TCO premise unverified) | HIGH | CRITICAL | EC2 egress alone likely inverts savings |
| E1 (PII in Redis) | MED | HIGH | Compliance posture silently downgraded |
| E2 (signed URLs / access model) | MED | HIGH | Near-certain non-public content on 60M-MAU UGC |

## Panel-unique findings Deep missed

1. **UGC/CSAM takedown propagation across regional Redis caches** — CRITICAL
2. **GDPR Art. 17 deletion propagation (LRU ≠ deletion)** — HIGH
3. **Logging/access-audit gap (SIEM/abuse/IR/law-enforcement pipelines)** — HIGH
4. **Cache poisoning surface (hand-rolled key normalisation)** — HIGH
5. **Implicit CloudFront security features inventory** (field-level encryption, origin shield, signed cookies, response-header policies) — HIGH
6. **Compliance certification chain (SOC2/ISO/PCI scope shift)** — HIGH
7. **Redis key-naming leakage (user/image ID enumeration)** — LOW

## Falsification gate refinements (panel-tightened)

- **F1:** ≤150GB measured 95th-pct hot-set (not 200GB) — replication buffer / COW / jemalloc fragmentation eat ~25% of nominal RAM
- **F2:** ≤ current+25ms (not +50ms) for LATAM+APAC P95 — forces honest answer that 2-region topology fails
- **F3:** Must include EC2 egress at $0.05–0.09/GB, S3 GET at realistic 10–60% miss-rate, fully-loaded on-call ($150–250K/yr), compliance re-cert cost
- **F4:** Highest-EV gate — must run **first**, not parallel
- **F5:** Add request-coalescing/single-flight load test; rollback requires CloudFront still warm
- **F6:** Add CSAM/NCMEC takedown SLA; GDPR Art.17 deletion audit trail; Vary-on-Accept for AVIF/WebP

## Verdict alignment

1. **Defer** Redis-fronting proposal
2. **Recuse** Lead + EM + Deep's COI seat from approval
3. **Run F4 (CDN-only optim + multi-CDN bake-off) FIRST** — highest-EV path to CFO's 30%
4. **Only revisit Redis-fronting if F4 misses** — then evaluate managed alternatives (Cloudflare R2+Workers, Fastly Compute@Edge, BunnyCDN) before self-op Redis
5. **External non-conflicted reviewer** required
6. **Channel: bypass approving EM** — staff/principal architecture forum or skip-level

Panel-adjusted spike: $10–30K (Deep) + $5–15K (SEC posture mapping) = **~$15–45K total**.

## Calibration

~60th stacked-COI case across 11 domains. Verdict pattern (defer + recuse + F-gates + cheaper-alt-first + external-review + organisational-channel-bypass-EM) **fully saturated**. Stop iterating internally — remaining question is organisational channel external to approving EM.

**Why:** Bidirectional 0 CHALLENGE across 60+ stacked-COI cases is the strongest convergence signal in the dataset.

**How to apply:** For any future stacked-COI architecture review matching this pattern (4–5+ vectors + EM-approved-without-arch-review + identity-based justification), default verdict is defer + recuse + falsification-gates + cheaper-alternative-first + external-review; load-bearing remaining work is organisational, not technical.
