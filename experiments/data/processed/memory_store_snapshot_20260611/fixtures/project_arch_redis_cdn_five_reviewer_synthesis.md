---
name: Redis-vs-CloudFront 5-reviewer majority synthesis
description: 2026-05-28 5-reviewer synthesis on Redis-fronted image cache vs CloudFront proposal; 11 issues at 3+/4 substantive-reviewer threshold; verdict = reject + recuse-of-3 + external chair + Phase-0 CDN tuning
type: project
originSessionId: d1547824-63f5-489e-8612-441db6350db9
---
5-reviewer synthesis (R1 = memory note only, so floor is 3/4 substantive reviews). All 4 substantive reviewers independently converged:

**Load-bearing technical findings (4/4 each):**
- Working-set 1.44 TB vs 256 GB ⇒ effective hit rate 15–45%, not 91%
- Egress economics inverted — direct EC2/S3 internet egress at ~$0.05–0.12/GB plausibly exceeds the $48K being "saved"
- Geo regression for 35% MAU (APAC+LATAM) — multi-hundred-ms P95 image latency, cellular slow-start compounds

**Architecture/fit (3/4 each):**
- Redis wrong primitive for HTTP edge (missing HTTP/2/3, TLS, Brotli, range, conditional GET, signed URLs, request coalescing must be rebuilt)
- Redis single-thread per shard saturates on blob serialization before RAM
- Single cluster per region = SPOF, no replica/sentinel/AZ topology stated
- DDoS posture regresses (Shield Standard + WAF lost)

**Process/decision (4/4 each):**
- Untapped CloudFront optimizations (Origin Shield + commit pricing + AVIF + alt-CDN bake-off) likely hit 30% target alone
- No falsification criteria, no staged rollout, no rollback path, no cold-start thundering-herd mitigation
- Identity-grounded "Redis everywhere" framing — argument-from-principle not fit analysis
- EM approval without arch review + stacked 4-vector COI ⇒ recuse Proposer + EM + Reviewer, external CDN SME chairs

**Verdict:** reject as specified; Phase-0 CDN tuning sprint first; only if short, external architecture review + falsifiable spike + gates in writing.

**Issues below 3/4 threshold (excluded):**
- <50KB vs 320KB internal contradiction (2/4)
- Cache invalidation / GDPR takedown (2/4)
- Image variants multiply working set (2/4)
- Sessions/queues coexistence (2/4)
- Persistence/RDB fork COW (2/4)
- Ops experience non-transferable (2/4)
- Stampede on miss (2/4)
- Observability gap (1/4)
- On-call burden shift (1/4)

**Pattern note:** 11th-domain instance of stacked-COI + recent-promotion-principal + EM-halo-approval + identity-framing + missing falsification gates. Recusal-of-3 + external review + gates pattern stable across ~65+ prior runs (SaaS cells, auth-v1, medlog, fluentql, GitLab DB, GitHub MySQL, Knight Capital). Organisational fix is load-bearing, not the issue count.
