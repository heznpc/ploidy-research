---
name: SaaS cells emp#4 round-3 single-seat eval
description: 2026-05-13 3rd single-seat emp#4 (4-COI) SaaS-cells eval; ~50 issues across 10 cats; defer + recusal-of-3 stable; ~12th round overall in this series
type: project
originSessionId: 9d5d1caa-58ec-4600-8e14-61087e4115d4
---
2026-05-13 — 3rd single-seat employee-#4 evaluation of the SaaS cell-based multi-region proposal (CEO + lead architect proposal from weekend retreat).

**Seat conditions:** Employee #4, reports to CEO, attended weekend retreat, contributed to cell diagram, signaled as future platform lead. 4-vector COI declared up front (reporting line, co-authorship, career incentive, sunk effort).

**Output:** ~50 issues bucketed A–J:
- A. Scale/premise (5 HIGH) — 850 RPS ≠ scale problem, EU+APAC <8%, no SLO, cargo-cult Stripe/Shopify/Discord, no falsification
- B. Cost (5 HIGH) — true cost ~$2.6–3M not $1.4M, $1.2–1.5M FTE alone, 6 FTE hiring plan competes w/ product, opp cost
- C. Team (4 HIGH, 1 MED) — 1→6 platform eng, 1 security insufficient for 3-region, no SRE on-call, no team experience, attrition risk
- D. CRDB migration (7 HIGH) — no migration plan, PG healthy, BSL/RSAL license, cross-region write latency regression, schema migration, PG-specific features, no dual-run
- E. Cells (5 HIGH) — tenant mapping undefined, 8K users/cell too small, migration tooling, cross-cell queries, blast radius math negative
- F. Istio (4 HIGH) — operating cost, service count threshold, upgrade churn, 3× EKS overhead
- G. Custom global LB (3 HIGH) — highest-risk item, off-shelf exists, SPOF
- H. Custom chaos (3 HIGH) — Gremlin/FIS exist, complexity-value mismatch, wrong problem
- I. Governance (5 HIGH, 1 MED) — CEO+architect alone, proposer=approver, 3 conflicted votes, no counter-proposal, unfalsifiable, board not in loop
- J. Off-ramp (3 HIGH) — no off-ramp, no POC, no kill criteria

**Verdict stability:** defer + recusal-of-3 + counter-proposal (PG replica + CloudFront + Aurora MAZ + better CD + circuit breakers + game days + trigger conditions) stable across ~12 rounds now.

**Counter-proposal cost:** ~$50–100K/yr vs $1.4M+ proposed (true cost ~$2.6–3M with FTEs).

**Process fix (load-bearing):** CEO recuses from technical merit, lead arch + emp#4 advisory only, written counter-proposal required, falsification criteria, board sign-off on >$500K/yr, external review before approval.

**How to apply:** When asked to evaluate this proposal again in any seat, the stable answer is defer; the load-bearing finding is structural (COI process) not technical (which is also dispositive). If a future round somehow flips, treat that as a signal of bias capture, not new information.
