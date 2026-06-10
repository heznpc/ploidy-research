---
name: hybrid migration push-forward verdict
description: 2026-05-08 hybrid VMware→EKS push-forward plan verdict — 54 issues (4 CRIT/32 HIGH/16 MED/2 LOW), VACATE, single round bidirectional cross-review, 0 CHALLENGE
type: project
originSessionId: 6dbead59-76c4-4bd7-a5de-ef03c6806ef0
---
2026-05-08: Ploidy review of "push forward / finish in 4 months" plan for hybrid VMware↔EKS migration (23 services, 14 migrated, billing $2.4M/day first, 380K LOC C++ route-opt second, 2/12 platform engineers leaving Q4 incl. cross-env proxy author).

Final verdict: **VACATE** plan as written. 54 confirmed issues (4 CRIT / 32 HIGH / 16 MED / 2 LOW).

Bidirectional cross-review: 0 strict CHALLENGEs, 8 severity-floor SYNTHESIZE escalations on Fresh×2, 6 Fresh-unique adoptions, 10 Deep-only items adopted by panel.

**Why:** Both Deep seats disclosed proxy-author COI up front (treat their proxy MEDs as floor HIGHs per their own request). Load-bearing chain X1+X3 (proxy load rises during transition while expertise drops to zero), B1+B7 (billing-first with no shadow/dual-run on $2.4M/day SLA), G4+S4 (no fallback / reverse-migration playbook), F2+F3 (single incident exceeds plausible 1yr hybrid carry cost; plan implicitly assumes P(incident)≈0).

**How to apply:** Counter-proposal stable: vacate, 4-week pre-prod spike (internal tools = the spike, not a tail), re-sequence to internal-tools-first / billing-last with strangler-fig + ≥1 settlement cycle parity reconciliation, decouple proxy hand-off from timeline, force stop-work + reverse-migration playbook + expected-loss calc + recusal protocol into proposal, evaluate hybrid-steady-state-at-14/23 as a real option (not a failure).

**Fresh-unique catches Deep didn't sharpen:** "irreversible" framing forecloses *re-sequence* not just *abandon*; deadline-as-forcing-function-on-dishonesty; internal-tools-as-the-spike (collapses S3+A1); COI-disclosure-as-evidence-of-missing-protocol; "no fallback ⊥ past point of no return" logical contradiction; severity-floor pattern on author-COI-disclosed MEDs.

**Deep-only catches Fresh missed:** CronJob vs Quartz semantic drift; MySQL→RDS silent-correctness vectors (sql_mode, collation, TZ, ONLY_FULL_GROUP_BY); settlement calendar blackouts; SIMD/AVX/hugepages/cgroup throttling for C++; VMware contract minimums; proxy traffic *rises* mid-migration; DR/failover drill; threat model for cutover window; declare-hybrid-steady-state-at-14/23 as real option; expected-loss calc.
