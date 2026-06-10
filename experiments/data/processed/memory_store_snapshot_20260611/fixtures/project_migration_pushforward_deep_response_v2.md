---
name: migration push-forward Deep×2→Fresh×2 round-2
description: 2026-05-08 round-2 cross-review on VMware→EKS push-forward; proxy-author COI seat; 1 severity CHALLENGE, 6 SYNTHESIZE escalations, 18 Deep-only persistent items, 6 Fresh-unique adoptions
type: project
originSessionId: 4f0af314-0d15-42cc-888b-d56ab71a6873
---
Round-2 Deep×2→Fresh×2 cross-review on push-forward migration plan (proxy-author seat, COI declared up front).

**Outcome:**
- 0 strict CHALLENGEs
- 1 severity CHALLENGE: F2-10 observability MEDIUM→HIGH (F1-7 had it right)
- 6 severity-floor SYNTHESIZE: incident trend (M→H), sunk-cost frame (M→H), success criteria (M→H), proxy-as-long-term-liability (conditional H), secret mgmt for billing (M→H for billing-first), F2-12 conditional escalation
- ~28 AGREE direct overlap

**6 Fresh-unique adoptions (this round):**
- F1-10: "largest first vs revenue-crit late picks the worst combination" — cleanest single-sentence governance critique
- F2-2: 14-already-migrated → billing is a step-change, not a continuation
- F2-3: /proc assumptions, core-dump handling, signal handling for C++ K8s packaging — Deep-quality specifics
- F2-6: data migration is "core of the work, not a footnote" for money-movement
- F2-7: no numerical SLA → can't decide cutover-window acceptability (error-budget axis)
- F2-8: CTO framing forecloses stabilizing hybrid as the cheapest option
- F2-15: cross-env DB calls persist post-billing → connection pooling + transaction semantics across proxy

**18 Deep-only persistent items:**
1. Team-lead proposal "under review" after CTO publicly anchored = theatre
2. $2.4M/day blast-radius framing for rollback gap
3. Stop-the-line criteria absent → "feel the pain" unfalsifiable
4. COI not surfaced in proposal record (proxy author = me)
5. Service-dependency graph absent → billing-first may *increase* proxy load
6. In-flight settlement reconciliation across cutover (idempotency/dedup)
7. SOX/PCI-adjacent audit trail during hybrid migration
8. NUMA / CPU-pinning / hugepages / cgroup-OOMKill for CPU-bound C++
9. Proxy traffic patterns shift unpredictably as services migrate
10. Proxy timeout incident root-cause closure status unknown
11. Proxy under-tested for current+projected scale (author self-assessment)
12. Cross-env identity model fragility (mechanism, not symptom of secret drift)
13. Replication lag sub-second requirement for time-of-day settlement; topology over VPN/Direct Connect
14. PITR / backup strategy across hybrid during migration window
15. Backfill hiring 3+ months — covers none of the critical window
16. Burnout / further-attrition risk under 6 months of "feel the pain"
17. VPN / Direct Connect throughput headroom not modeled
18. Customer-portal split-brain (write legacy / read EKS) — consistency/cache invalidation

**Pattern recurrence:** 3rd embedded-engineer single-seat eval (after fluentql, medlog). Same pattern: COI declaration up front shifts analysis to structural critique rather than defending the in-flight plan.

**Fresh systematic gap (consistent across rounds):** severity-floor under-grading on consequence-chain items, especially governance frames that disable downstream checks (sunk-cost, success-criteria absence, observability during cutover).

**Load-bearing chain (4-seat convergent):**
1. Sunk-cost CTO frame disables all downstream checks
2. Billing-first inverts revenue-crit-late + risk-laddered ordering
3. No rollback for $2.4M/day blast radius
4. Proxy bus-factor: author leaving + me (proxy author) reassigned to billing
5. 17% attrition + 4-month deadline + two hardest services concurrent → capacity fiction

**Verdict (stable across rounds):** Do not migrate billing first. Re-sequence behind 2–3 internal tools + lower-stakes legacy. Route-opt packaging as separate workstream. Recuse proposal author + proxy author. Gated milestones + stop-the-line criteria, not deadline.
