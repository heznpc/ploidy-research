---
name: SaaS Architecture Evaluation — Cell-Based Multi-Region Proposal
description: 200K-user B2B SaaS evaluating CEO/architect cell-based multi-region proposal; identified 22 critical-to-moderate issues; defer recommended
type: project
originSessionId: a1048686-17df-42a7-941a-2c260ad3a052
---
## Proposal Summary
- **Current**: 200K users, 850 RPS, single PostgreSQL, $94K/yr infra, 1 platform engineer
- **Proposed**: 3 regions (us-east, eu-west, ap-northeast), 8 cells per region, Istio service mesh, CockroachDB, custom load balancer, internal chaos framework
- **Estimated cost**: $1.4M/yr infra + $1.2M–$1.5M/yr headcount (6 platform FTEs)
- **Stated rationale**: "Scale to 10M users without re-architecture; Stripe/Shopify/Discord do this"

## Top-Line Verdict
**DEFER. Proceed with High Risk.**

Premature adoption of scaling architecture for company with zero scaling pressure. 15× cost increase + team fragmentation for hypothetical future problem. Retrofit strategy is standard industry practice.

## Critical Issues (HIGH confidence)

### 1. Scale Mismatch: Premature Architecture
- 850 RPS in single region; PostgreSQL handles 5K+ RPS routinely
- p99 latencies (12ms read, 38ms write) show zero contention
- Cell-based is a *scaling solution*; you don't have a scaling problem
- **Confidence**: HIGH (observable in metrics)

### 2. Team Capacity Insufficient
- Proposal requires 6 platform FTEs; you have 1
- Hiring cycle: 6 months minimum; cost per FTE: $200K–$250K loaded = $1.2M–$1.5M/yr
- Will require pulling 2–3 backend engineers into platform work (product velocity tax)
- **Confidence**: HIGH (staffing math is objective)

### 3. Istio Operational Risk
- Control plane sync issues across regions; no out-of-the-box federation at 2026 maturity
- mTLS cert rotation bugs across regions (documented in Istio incidents)
- Sidecar density overhead: 24 cells × N pods = hundreds of Envoy processes (100MB+ RAM each)
- Observability: distributed tracing across regions requires external backend (Jaeger, Tempo, Datadog = $5K–$20K/mo additional)
- **Confidence**: HIGH (well-documented in CNCF case studies)

### 4. CockroachDB Migration Functional Risk
- Uses Raft consensus, not PostgreSQL MVCC; applications must handle serialization conflicts
- ORMs have known gotchas (transaction retry logic, specific query syntax incompatibilities)
- Full table locking during migration = production downtime risk
- Will discover PostgreSQL-isms in application code post-migration
- **Confidence**: HIGH (standard DB migration + behavioral differences)

### 5. Regional Over-Provisioning
- eu-west + ap-northeast = <8% of traffic
- 8 cells per region means 7+ idle cells in low-traffic regions
- Multi-master replication: write-amplification (every transaction commits to 3 regions); p99 write 38ms → 80ms–120ms
- **Confidence**: HIGH (traffic data is concrete)

### 6. Custom Global Load Balancer: SPOF Risk
- Bug in routing logic breaks all 3 regions simultaneously
- Failover behavior undefined (degraded vs. dead cell? timeout for health checks?)
- Cross-region consistency of routing state requires distributed consensus (not mentioned)
- **Confidence**: HIGH (distributed systems failure modes are well-known)

## Major Issues (HIGH confidence)

### 7. Incident History Does Not Justify
- 2 incidents in 6 months, neither infrastructure-related (deploy bug, third-party API)
- This architecture doesn't prevent deploy bugs or third-party failures
- Only addresses geographic failover (which you don't need yet)
- **Confidence**: HIGH (incident root causes are documented)

### 8. Cost Explosion
- Infra: $94K → $1.4M/yr (15×)
- Headcount: $0 → $1.2M–$1.5M/yr (6 platform FTEs)
- **Total**: ~$2.6M/yr
- Break-even: requires 2.7× revenue growth just for platform costs
- **Confidence**: HIGH (finance is deterministic)

### 9. Cell-Based Requires Sharded Data Model
- Assumes data can be partitioned (tenant_id, shard_id, etc.)
- Application logic to route to correct cell (non-trivial)
- Cross-cell joins become impossible
- Shard rebalancing for hotspots is operationally expensive
- If schema is not shard-ready: 3–6 month refactoring required
- **Confidence**: HIGH (sharding is hard requirement, not optional)

### 10. Chaos Engineering Framework: Operational Tax
- "Internal-built" means engineering tax on your small team
- CNCF tools (Gremlin, Chaos Mesh) are mature; using them saves 2 FTE months
- Proposal explicitly specifies internal build (not cost-justified)
- **Confidence**: MEDIUM-HIGH

## Significant Issues (MEDIUM-HIGH confidence)

### 11. Observability Tooling Gaps
- Distributed tracing (Tempo, Datadog, Honeycomb): $5K–$20K/mo
- Metrics aggregation: Prometheus cardinality explosion with 24 cells
- Alerting: cell-level vs. regional vs. global failure distinction is complex
- Estimated effort to implement: 2–3 FTE months
- **Confidence**: MEDIUM-HIGH

### 12. Backup & Disaster Recovery Undefined
- CockroachDB backup semantics differ from PostgreSQL (incremental, consistency guarantees change)
- Multi-region backups must be cross-region stored + tested regularly
- Proposal mentions neither strategy nor RTO/RPO targets
- **Confidence**: MEDIUM-HIGH (absence from proposal is red flag)

### 13. Network Latency & Consistency Tradeoffs
- Multi-master replication: 100ms+ round-trip for Raft consensus
- Strong consistency reads require quorum (not feasible for time-sensitive ops)
- Weak consistency reads create stale data windows
- Proposal doesn't specify consistency model or acceptable staleness
- **Confidence**: MEDIUM-HIGH (CAP theorem tradeoff)

### 14. EKS Multi-Region Federation
- No out-of-the-box federation (unlike Google GKE)
- Cross-cluster service discovery requires custom tooling or Istio federation (still beta)
- Rolling updates across 3 regions: complex canary strategy required
- DNS failover (Route53) is not instantaneous
- **Confidence**: MEDIUM-HIGH (EKS limitations documented)

## Moderate Issues (MEDIUM confidence)

### 15. Developer Experience Regression
- Onboarding: 4–6 weeks vs. 1–2 weeks
- Local dev environment: cell simulation or staging access required
- Debugging cross-region failures requires distributed tracing expertise (uncommon)
- Velocity loss during transition
- **Confidence**: MEDIUM

### 16. Upgrade & Patch Management
- Istio control plane upgrades across regions (coordination complex)
- EKS cluster version upgrades (downtime coordination)
- CockroachDB rolling restarts (state verification required)
- Proposal assumes zero-downtime rolling; aspirational without testing
- **Confidence**: MEDIUM

### 17. Compliance & Data Residency
- EU user data stored in us-east-1 by default (GDPR violation if not isolated)
- Cell-based must enforce data locality (tenant data in region only)
- Compliance auditing, encryption at rest/in transit not mentioned
- **Confidence**: MEDIUM (depends on your compliance scope)

### 18. "Future-Proofing" Fallacy
- Proposal: "Build now while small to avoid retrofit later"
- Reality: Retrofit when constraints are real, not hypothetical
- At 10M users, infrastructure assumptions will differ (newer tech, different paradigms)
- Stripe/Shopify/Discord retrofitted at 1M+; you're at 200K
- **Confidence**: MEDIUM-HIGH (well-known engineering fallacy)

### 19. Stripe/Shopify/Discord Comparison Invalid
- Stripe: payments (high-volume, low-latency critical); cells are isolation, not capacity
- Shopify: 850K merchants (4× your users); needed cells earlier
- Discord: social platform (hundreds of millions concurrent); not comparable
- Proposal name-checks without explaining *why* their architecture fits
- **Confidence**: MEDIUM-HIGH

## Unknowns (MEDIUM confidence)

### 20. Cell Splitting Strategy
- How will you split cells as traffic grows in a region?
- Double the cell count (8 → 16)? Rebalance tenants between cells?
- Automation or manual?
- **Proposal answer**: Silent
- **Confidence**: MEDIUM

### 21. Rollback Strategy for Global Outages
- If bad deploy hits all 3 regions simultaneously, what's the rollback plan?
- Cross-region coordination required? Manual intervention per region?
- Rollback time target?
- **Proposal answer**: Silent
- **Confidence**: MEDIUM

### 22. Cost Attribution by Geography
- Current: simple ($94K single region)
- Proposed: opaque (how much of $1.4M is EU vs. shared overhead?)
- Matters for P&L by region, pricing decisions, licensing
- **Proposal answer**: Silent
- **Confidence**: MEDIUM

---

## Recommended Alternative Path

1. **Now (200K users, 850 RPS)**: Add standby PostgreSQL in us-east-1 for HA; implement read replicas for analytics. Cost: $150K/yr. Effort: 2 FTE weeks.

2. **When 3K RPS or 5M users**: Implement application-level sharding by tenant. Stay single-region until international traffic >30%. Cost: $300K/yr infra + 2 FTE months engineering.

3. **When 20M users**: Evaluate cell-based multi-region with mature team (20 platform engineers), clear sharding strategy, proven observability. Cost: $1.4M/yr is justified.

---

## Why This Matters

Proceeding with this proposal risks:
- **Sunk cost ratchet**: $2.6M/yr spend will be hard to reverse
- **Premature specialization**: Team becomes experts in Istio/CockroachDB/cells instead of product
- **Hidden constraint discovery**: Midway through, you'll learn the *real* bottleneck was something else (e.g., analytics pipeline, not transactional database)
- **Opportunity cost**: 6 platform FTEs could build 3–4 major product features instead

Deferring is lower risk. Retrofit when scale *demands* it, not when strategy imagines it.
