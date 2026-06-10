---
name: arch logistics-migration platform-eng COI seat round 2
description: 2026-05-14 2nd-pass platform-eng 5-vector COI seat eval of on-prem→EKS push-forward plan; ~32 issues + F1-F6 gates; defer + recuse-proxy-authors + re-sequence stable; 7th stacked-COI case
type: project
originSessionId: 4f24c52a-03f2-4835-b930-5293e58c4c68
---
2026-05-14: 2nd round on the logistics on-prem VMware → AWS EKS push-forward plan from a platform-eng seat with stacked COI (proxy author + 6mo team + leaving peer = closest collaborator + nodded at CTO's "past point of no return" framing + codebase identity).

**5-vector COI declared up front.** F1–F6 falsification gates committed before issue list:
- F1 billing rollback to VMware MySQL with tested RTO ≤ 1h
- F2 route-opt K8s packaging has working dev-cluster build
- F3 last-quarter cross-env incidents RCA'd and fixed (not just identified)
- F4 proxy bus-factor mitigated (≥1 other engineer has shipped to it in 90d)
- F5 4-month estimate is bottom-up with confidence interval, not top-down from CTO framing
- F6 billing on EKS load-tested at ≥1.5× peak with realistic replication lag

**~32 issues across A–G:** sequencing (billing-first is worst possible first move; route-opt mis-sequenced; no stop-the-bleed-first; no per-service rollback), estimate (4mo matches CTO verbatim; 14/23 in 6mo projects worse on legacy core; attrition concurrent with hardest 40%), SRE (observability silos, proxy SLO absent, RDS↔VMware MySQL topology undescribed), service-specifics (billing time-of-day SLA, 380K LOC C++ packaging uncosted, write-path data-loss exposure, gRPC streams), people (recuse proxy authors, CTO framing pre-empts dissent, no platform stabilisation capacity), cost (no E[outage cost] framing, optimising-for-what unstated), process (no kill criteria, no external review, single-track plan).

**Verdict stable:** defer billing-last + stabilise hybrid 4–6 weeks first + decouple route-opt packaging as separate workstream + recuse proxy authors from sequencing + document kill criteria + external SRE review. ~$N counter-proposal not estimated this round.

**Why:** 7th stacked-COI case after saas-cells (rounds 1–16+), medlog, arch-split (rounds 1–24+), auth-v1 (rounds 1–4), pg-optim, and round-1 logistics. Verdict converges on same shape: defer-irreversible-step + recuse-conflicted-authors + name-kill-criteria + falsification-gates-before-issues. Pattern is now stable enough to count as a finding worth folding into the paper: COI-declared reviewing with pre-committed falsification gates produces stable verdicts independent of domain.

**How to apply:** future stacked-COI arch reviews — keep the same protocol (declare COI vectors, commit falsification gates, then issues with HIGH/MED/LOW). Don't iterate beyond the second pass — verdict was stable from round 1, second pass adds detail not direction. Remaining question is organisational (how to get the decision channel external to the CTO who framed it), not technical.
