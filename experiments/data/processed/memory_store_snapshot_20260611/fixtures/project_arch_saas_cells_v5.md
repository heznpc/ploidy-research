---
name: arch saas-cells v5 cross-review
description: 2026-05-13 round-5 Deep×2→Fresh×2 cross-review on SaaS cells (per-point); 0 CHALLENGE, ~13 severity-floor SYNTHESIZE, 14 Deep-only persistent items, verdict stable across 5 rounds
type: project
originSessionId: 80039f07-e980-4ea5-8c20-781588ac79e0
---
Round 5 cross-review on the SaaS cell-based arch proposal (200K users, 850 RPS, Series-A, $94K→$1.4M infra, 1→6 platform FTEs).

Seat: employee-#4 + future-platform-lead (stacked COI; recused from approval, technical review only).

**Pattern unchanged from v4**: 0 strict CHALLENGEs, ~13 severity-floor SYNTHESIZE escalations (Fresh under-grades consequence-chain items MED→HIGH), 14 Deep-only persistent items. Recommendation stable: DO NOT PROCEED.

**Severity escalations adopted from Fresh in this round:**
- Istio overhead (F1-11) MED → HIGH (1 platform eng cannot own control plane + mTLS rotation)
- Sec eng 1 × tripled surface (F1-12) MED → HIGH
- Opportunity cost on product (F1-15) MED → HIGH (Series-A PMF stage)
- "Avoid retrofitting" false economy (F1-14) MED → HIGH (unfalsifiable at 10M)
- Cost estimate floor (F1-18) MED → HIGH (cross-region egress + RSALv2 license unaccounted)
- Observability/SRE practice (F1-19) LOW → HIGH (24× surface, current stack does not multiply)
- Hiring 6 platform eng (F1-20) LOW → HIGH (prerequisite, not afterthought)
- Data residency / compliance (F2-18) MED → HIGH if any commitment exists
- Cross-region consistency model (F2-19) MED → HIGH
- Chaos framework (F2-10) MED → HIGH (no SRE to respond)
- Weekend retreat origin (F1-16, F2-11) → CRITICAL
- No incremental/reversible path (F2-20) → CRITICAL
- Platform headcount 6× (F2-4) → CRITICAL ("the org changes shape")

**Fresh-unique catches this round (adopt):**
- F2-5 "Who pages at 3am when EU Istio control plane partitions?" — sharp on-call framing
- F2-7 CRDB serializable-only breaks code written against PG read-committed → retry loops in app
- F2-8 "Companies routinely staff 2-4 engineers just to run Istio" — concrete
- F2-9 Custom GLB ≈ 1-2 FTE-years for no differentiation
- F2-13 Three sub-points on "avoid retrofitting": re-arch at 2M easier; existential burn now; YAGNI for infra
- F2-14 "Aspirations not problems" meta-frame on whole proposal
- F1-3 / F2-4 reframing: 6 platform hires is not "hire-and-onboard," it's "the entire eng org changes shape"

**14 Deep-only items Fresh×2 missed (zero-context cannot see):**
1. COI #0 — recusal of 3 authors (CEO + lead architect + me) from deciding vote; load-bearing structural fix
2. Cell-shared data (auth, billing, global config) — Stripe/Shopify have whole teams on this
3. Cell-router / placement / tenant→cell mapping / hot-cell migration / cross-cell query rejection tooling absent
4. Background jobs / queues (Celery/Sidekiq) not natively multi-region
5. Object storage cross-region replication cost + consistency
6. Multi-region networking sub-discipline absent (TGW, VPC peering, DNS, cert mgmt)
7. CockroachDB RSALv2 / CCL legal review surface unaddressed
8. PG → CRDB migration *strategy* (dual-write / cutover) missing
9. Anycast vs DNS-routing failure modes (TTL caching, BGP flap)
10. Unfalsifiable framing ("punching above our weight" / "10M without re-arch") should be excluded as evidence
11. Reverse-migration cost as precondition (CRDB→PG multi-quarter)
12. Staged commitment with falsifiable re-triggers (RPS>5K sustained / signed EU residency contract / PG write p99>100ms × 14d)
13. Promotion-as-architecture-portfolio (personal financial incentive on record)
14. Frontend (2 devs) inherits multi-region conflict-resolution semantics

**Cost calibration (carried from v4):** loaded run-rate ~$3.2M/yr ($1.4M infra + $1.8M people at $300K loaded SF/NYC); year-1 ramp + license + egress pushes to ~$3.5–4M.

**Counter-proposal stable across 5 rounds:**
- Stay single-region us-east on RDS PG + read replica per region for <8% non-US
- CDN tier-up (origin shield, longer TTLs, immutable URLs)
- Spend platform headcount on deploy safety + circuit breakers + runbooks (matches actual failure history)
- 1 incremental platform FTE not 6
- Falsifiable re-trigger criteria
- Process fix: written RFC, comparison-of-alternatives, dissent log, falsification criteria, author recuses on vote
- Total: ~$450K/yr vs proposed ~$3.2–4M

**Why:** Round-5 produced 0 CHALLENGEs and 0 new Deep-only items beyond the 14. Convergence is real; further rounds will not change verdict.

**How to apply:** When this question recurs, cite v3+v4+v5 convergence; do not re-run the panel. Proceed to structural fix (recusal vote, external reviewer, RFC with alternatives + falsification + reverse-off-ramp).
