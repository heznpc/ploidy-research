---
name: arch_redis_cdn_replacement
description: 2026-05-28 — stacked-COI seat (4-vector: peer+promotion-committee+EM-hired+sunk-tool) evaluating Redis-cluster-replaces-CloudFront proposal for 60M MAU consumer marketplace image CDN; first non-SaaS-cells / non-auth-v1 domain in the architecture-debate stacked-COI series
type: project
originSessionId: 2ed57f74-925b-4d3f-8cdb-2ed8e2395797
---
**Seat**: backend eng, 4yr peer of Redis-core-contributor Lead, promoted-by Lead (committee), hired by approving-EM, 4yr operator of existing Redis session/queue stack.

**Proposal**: Replace CloudFront ($48K/mo, 91% edge hit ratio) with 2-region Redis cluster (256GB each, us-east + eu-west), LRU, S3 fallback. Lead's framing: "own your stack, Redis everywhere is the principle." EM approved without arch review.

**Key technical findings** (HIGH unless noted):
- **Capacity**: 8M × 180KB WebP P50 = 1.44TB working set; 512GB total RAM = 21–36% of working set; LRU cannot reproduce 91% CloudFront aggregate-edge hit ratio. Realistic 60–75%.
- **Latency**: 2 regions for NA 35% / EU 30% / LATAM 18% / APAC 17%. Plan turns *current* cold-miss RTT (480ms APAC) into the *warm-path* RTT. CloudFront edge POP count is the actual product being replaced.
- **Cost**: dominant cost is egress, which does NOT disappear and at EC2 prices (~$0.09/GB) often exceeds CloudFront tiered. Worse hit ratio → more S3 GETs. Plus Redis nodes + replicas + LB + observability. 30% saving claim unsubstantiated; net cost likely increases year 1.
- **Tool fit**: Redis is wrong for 180KB–1.8MB blobs. RESP overhead, single I/O thread, fork() on 256GB RSS, slow BGSAVE/AOF rewrite, blocking slot migration, no HTTP semantics (Range, ETag, Vary, DPR), hot-key amplification on single shard.
- **Principle argument**: brief says avg 320KB / P50 180KB / P90 1.8MB — Lead's "most images <50KB" premise is factually wrong against the workload spec.
- **Process**: Lead = Redis core contributor + last-quarter principal promotion = role-resume conflict. EM approved on personal trust, not review. I am structurally non-neutral.
- **Unexplored alternatives**: CloudFront commit-bid, AVIF, Origin Shield, responsive-size caps for mobile, multi-CDN bidding.

**Verdict**: decline / send back, BUT delivered through process not by me — recuse Lead+EM+me, external arch review by uncompromised staff/principal, 4 falsification gates (hit-ratio shadow, APAC P50, TCO model, ops runbook).

**Why this matters for paper**:
- First **non-SaaS-cells, non-auth-v1** domain in stacked-COI architecture series.
- Reproduces same pattern: technical issues are nameable, but the load-bearing fix is *organisational* (recusal + external review + falsification gates) not technical.
- New artifact-internal contradiction class: proposer's stated workload premise ("most images <50KB") is contradicted by the workload spec in the same proposal (320KB / P50 180KB / P90 1.8MB). Analogous to Knight Capital R0 (artifact-internal contradiction = strongest with-artifact finding) and GitHub MySQL R0 (43>30 threshold contradiction).
- Confirms: artifact-internal contradiction is a domain-invariant load-bearing finding pattern across PG / MySQL / order-router / CDN-vs-cache 4 domains now.

**How to apply**:
- When future architecture debates land on me with stacked COI, declare 4-vector up front before technical content, same structure as auth-v1 and SaaS-cells series.
- Lift artifact-internal-contradiction pattern to paper as a domain-invariant with-artifact finding class.
