---
name: VMware→EKS migration final verdict
description: 2026-05-08 final consolidated VMware→EKS push-forward plan verdict — Deep×2+Fresh×2+bidirectional cross-review; 52 issues (11 CRIT/28 HIGH/12 MED/1 LOW); 0 strict CHALLENGEs; load-bearing chain anchored on sunk-cost framing + no rollback + inverted sequencing + proxy bus-factor + DB decoupling + split observability + top-down timeline + proposer COI; counter-proposal stable both sides
type: project
originSessionId: 4eadc585-1a54-4a3e-9f1e-88eb29944fa1
---
2026-05-08 — VMware→EKS migration plan, 4-reviewer Ploidy debate (Deep×2 + Fresh×2 + bidirectional cross).

**Verdict: DO NOT APPROVE AS WRITTEN.** 0 strict CHALLENGEs on substance.

**Severity counts:** 11 CRITICAL / 28 HIGH / 12 MEDIUM / 1 LOW = 52 confirmed issues.

**Load-bearing chain:**
A1 sunk-cost framing → A2/A3 no rollback/abort → B1–B3 billing-first inverted → F1 proxy bus-factor 1→0 → E1 DB-compute decoupling → G1 split observability → A5/H1 top-down timeline + 17% Q4 attrition → A7 proposer COI + no independent review.

**11 CRITICAL items:**
A1 sunk-cost; A2 no rollback; A3 no abort criteria; A7 proposer COI; B1 billing-first inversion; C1 EKS scheduler/jitter on time-of-day SLA; C3 billing-MySQL stays on VMware; D1 380K LOC C++ no K8s packaging; E1 DB-compute decoupling = permanent cross-env data plane; F1 proxy bus-factor 1→0 in Q4; G1 split observability during billing cutover; H1 17% Q4 attrition not in timeline math.

**Deep-only catches (12):** PCI/SOX scope re-attestation lead time; EKS scheduler/jitter as SLA-killer; C++ runtime specifics (THP/NUMA/OOMKill); Aurora vs MySQL replication semantics (GTID/parallel); rollback-time *budget* (financial exposure window); **vendor-cliff hypothesis** (is 4-month contractually driven?); RACI / on-call rota; tacit-knowledge model; trace propagation as named prerequisite; attrition cascade; proxy direction-inversion (EKS→VMware grows as migration progresses); finance daily-close dual-env tie-out.

**Fresh-only catches (5):** throughput arithmetic (2.25 services/mo on harder tail); deprecation-vs-migration scope cut for internal tools; "stabilize hybrid + selective migration" as named first-class strategy; replace-proxy-with-managed-mesh as first-class option; internal-tools-critical-path enumeration before bucketing.

**SYNTHESIZE (5):** A4 CTO commitment escalated MED→HIGH; A6 false-dichotomy → 3-bucket cost framing; B7 portal write-path → "may be masking latent bugs"; I1 cost model 2-bucket → 3-bucket; I2 readiness scorecard → enumerated columns.

**CHALLENGEs (2 partial):** D3 "5–30%" perf delta is illustrative not load-bearing (no source, workload-dependent); Deep1 self-flag on #19 — self-checking is not independent verification.

**Counter-proposal (stable both sides):**
1. Re-sequence: internal tools first, billing last among revenue-critical.
2. Route-opt on research track decoupled from cutover dates; "don't migrate" as first-class option.
3. Co-migrate DBs with services.
4. Unify observability before any revenue-critical cutover.
5. Document rollback + abort criteria per cutover, pre-committed thresholds.
6. Capacity-derived schedule (Deep's "6–9 months" illustrative not derived).
7. Transfer proxy ownership before Q4; consider replacing with managed mesh.
8. Independent (non-platform) reviewer for proxy and sequencing.
9. **Verify whether 4-month timeline is contractually driven** — if yes, conversation belongs with CFO not platform team.

**Why this matters / How to apply:**
The structural pattern is *proposer COI + sunk-cost framing + suppressed dissent* — the team writing the plan also built the load-bearing fabric (proxy) being grade-deferred. Every plan with this shape needs an independent reviewer named explicitly, plus a forced check on whether the timeline is engineering-derived or contractually-imposed.
