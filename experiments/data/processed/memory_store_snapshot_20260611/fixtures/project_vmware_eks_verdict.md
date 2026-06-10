---
name: VMware→EKS push-forward verdict
description: 2026-05-08 Deep×2+Fresh×2 verdict on 4-month VMware→EKS finish; REJECT as written; 34 issues (2 CRIT/19 HIGH/13 MED); load-bearing = no rollback + worst-first sequencing + timeline arithmetic + no cost ledger + VMware-as-rollback-substrate
type: project
originSessionId: 89266d75-e5aa-433e-b47b-040b6da19a02
---
2026-05-08 architecture debate on push-forward plan to finish VMware→EKS migration in 4 months starting with billing service ($2.4M/day, time-of-day SLA), 380K LOC C++ route-opt, 7 MySQL→RDS migrations, with 17% Q4 platform attrition including the cross-env proxy author.

**Verdict: REJECT as written.** Counter-proposal stable: observability-first stabilization quarter → EC2 lift-and-shift for route-opt → billing last via strangler-fig with documented rollback + proxy succession. Three preconditions: carrying-cost ledger, post-attrition capacity arithmetic, external-deadline confirmation.

**Why:** 34 confirmed issues, 0 strict CHALLENGEs bidirectional. Load-bearing chain = C1 (no rollback) + C2 (worst-first sequencing) + H3 (2.3/mo run-rate refutes 4-month claim) + H4 (17% attrition unbooked vs BAU+incidents) + H6 (no hybrid cost ledger) + H8 (sunk-cost framing) + H13 (hybrid-wasted vs proxy-must-grow contradiction) + H17 (VMware = rollback substrate) + H18 (billing depends on still-legacy services so billing-first *increases* cross-env traffic).

**How to apply:** Pattern continues prior architecture debates (arch-split, redis-cdn, fluentql, medlog) — Fresh systematically delivers run-rate arithmetic + dependency-graph reasoning + premise-refutation that Deep misses; Deep delivers internal contradictions (P3 type), governance/process critique, and negative findings (CQRS-not-accommodatable). Fresh under-grades consequence-chain items by one severity level on average.

Fresh-unique panel-wide gaps Deep both seats missed:
1. Run-rate arithmetic (2.3 services/month historical against harder remainder)
2. Capacity arithmetic with explicit 2/12 = 17% against BAU+incidents
3. VMware-as-rollback-substrate (premature decommission removes revert target)
4. Incident-rate *trend* not count as urgency-framing falsifier
5. Service-coupling-driven leaves-first ordering
6. Customer-portal split-brain (read-on-EKS + write-on-legacy stale-read)
7. Per-service go/no-go gates / done criteria
8. Concurrency (serial vs parallel) unspecified
9. Load/chaos testing as billing precondition
10. External-deadline-driver? question (only one that could reverse verdict)

Deep-unique panel-wide items Fresh both seats missed:
1. Internal contradiction "hybrid wasted" vs "proxy must carry more" (P3)
2. DB-service coupling = 2-axis change on billing
3. Idempotency/replay on settlement events
4. SLO baseline missing on legacy core
5. Incident-cost asymmetry vs hybrid carrying cost
6. All-hands ≠ architecture review; CTO-framed precludes "whether"
7. CQRS not freely accommodatable (no CDC/event-stream/outbox) — negative finding
8. Strangler-fig requires proxy-rework first
9. EC2 lift-and-shift for route-opt as decoupling lever
10. EKS-for-everything as sunk-cost assumption

Calibration call: stop iterating, ship verdict.
