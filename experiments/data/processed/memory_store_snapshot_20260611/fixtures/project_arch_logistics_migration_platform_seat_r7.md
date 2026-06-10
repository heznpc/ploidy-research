---
name: arch_logistics_migration_platform_seat_r7
description: 2026-05-14 7th-pass platform-eng 5-vector COI seat logistics-migration (~12th stacked-COI case); ~40 issues A–I + F1–F6; verdict stable; remaining Q is organisational
type: project
originSessionId: e06ef3dd-3bba-43ea-9c86-8ebc2320d7ef
---
7th-pass platform-engineer 5-vector COI seat eval of the on-prem VMware → AWS EKS logistics migration push-forward proposal (~12th stacked-COI case overall in this run).

**5-vector COI declared up front:** proxy author (month 2), 6 months on migration team, leaving peer = closest collaborator, nodded at CTO's "past the point of no return" framing, identity-coded as "the migration person."

**6 falsification gates up front (F1–F6):** billing rollback w/ 30-min RTO, route-opt K8s package soak-tested, proxy-author successor + 90-day overlap, cross-env incident trend down, signed CFO/COO settlement-risk acknowledgement, fallback plan with abort criteria.

**~40 issues across A–I:**
- A. Sequencing (billing-first inverts risk gradient, no DAG, internal tools should go first)
- B. Billing-specific (autoscaler cold-start vs ToD SLA, no RTO/RPO, settlement idempotency under dual-run, DB cross-env latency)
- C. Route-opt 380K LOC C++ (K8s packaging is months not checkbox, build pipeline, perf regression, accelerator parity)
- D. Cross-env proxy (bus factor → 0.5, timeout already incident class, no capacity headroom, retiring during peak load)
- E. Observability gap (Datadog/ELK split unacceptable mid-migration, log-correlation + secret-drift already incident classes)
- F. Capacity (17% headcount loss in Q4, proxy author leaving, 4-month plan has zero slack)
- G. Decision-process (coercive framing, false dichotomy, no fallback documented, in-room conformity, all reviewers conflicted)
- H. Missing analyses (no DAG, no cost comparison, no DR for cutover window, no bake time)
- I. Cross-env incident trend not reported

**Counter-proposal (stable across all 12 rounds):**
1. Reverse sequence: internal tools → customer-portal-write → GPS/fleet → billing + route-opt LAST
2. Stabilize hybrid before accelerating (unified obs, unified secrets, proxy capacity, successor + 90d overlap), ~$30–60K
3. Document fallback w/ abort criteria for every remaining migration
4. Recuse 3 most-conflicted voices (team-lead, proxy author, leaving peer); use external SRE/architect reviewer
5. Re-baseline timeline: 9–15 months not 4

**Verdict:** DEFER. Stable across ~12 rounds. **Why:** technical answer hasn't moved for 7 platform-seat passes + 5 broader passes; the remaining variable is governance/channel. **How to apply:** stop iterating internally on technical merits — further runs from in-group seats are redundant. Channel needs to be external to CTO's in-room consensus (consultant, board advisor, peer-company SRE). This is now a stable finding, like saas-cells, arch-split, auth-v1, medlog, pg-optim.
