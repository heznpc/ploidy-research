---
name: migration push-forward plan final verdict
description: 2026-05-08 Deep×2+Fresh×2 verdict on EKS migration push-forward plan — 64 issues, DO NOT APPROVE, load-bearing chain
type: project
originSessionId: a86c1357-a610-4b16-ac0d-fc7ba7455c18
---
# Push-forward EKS migration plan — final verdict (2026-05-08)

**Context:** Logistics company, 14/23 services on EKS for 6mo, 9 legacy services on VMware (incl. billing $2.4M/day TOD-SLA, route-opt 380K LOC C++ no K8s packaging, customer-portal-write, 7 MySQL replicas). CTO "past point of no return"; team-lead pushes 4-month finish, billing first. 2/12 platform engineers leaving Q4 incl. cross-env-proxy author; 3 incidents/quarter (proxy timeout, log correlation, secret rotation).

**Verdict: DO NOT APPROVE AS WRITTEN. Confidence HIGH.**

## Convergence stats
- ~64 issues: 3 CRIT / 36 HIGH / 22 MED / 1 LOW-MED
- 0 strict CHALLENGEs bidirectional Deep×2 ↔ Fresh×2
- 9+ severity-floor SYNTHESIZE escalations (Fresh systematically under-grades consequence-chain items — same pattern as fluentql/Redis-CDN/arch-split panels)
- ~38 Both / ~16 Deep-only (procedural+financial+2nd-order) / ~10 Fresh-only (decision-frame+meta)

## Load-bearing chain (any one justifies re-plan)
1. **B7+G3** absent fallback/reverse-cutover for $2.4M/day
2. **P1+P4+S4** proxy bus factor 1→0, no contracted 2nd author
3. **G6+S1** billing-first on unvalidated runbook
4. **R1+R2+S2** C++ packaging unbounded as slot #2
5. **G4+G5+M3** reviewer pool = work pool = sunk-cost population (disclosure ≠ mitigation)
6. **C1+C5** no decomposed cost model; "hybrid expensive" is rhetoric

## Fresh-unique decision-frame catches (Deep panel under-emphasized)
- M4 wrong question reviewed: binary approve/reject, missing "replan"
- M5 cutover decision-rights unspecified (who calls 3am go/no-go?)
- M6 origin of "4-month" anchor (FY/board/contract?) as hidden constraint
- M7 no falsification criteria for "on track"
- O4 plan has no observability for itself (no leading indicators)
- P5 proxy is *product* during migration, needs product-grade SLO
- S7 pause-and-stabilize as first-class off-ramp design
- T4 hiring lead-time: contractor gets 2-3mo overlap → must narrow proxy scope in parallel
- T5 "no return" framing plausibly accelerates Q4 attrition
- Co4 billing has external counterparties (banks/networks) needing contractual notification

## Deep-only procedural/financial catches Fresh missed
B3 in-flight settlement idempotency, B5 dual-run obs split during cutover window, B6 audit trail continuity (esc. HIGH), B8 to-the-cent reconciliation, R2 C++ build pipeline (CI cache, distributed build), R7 NUMA/hugepages/OOMKilled, O2 distributed traces don't cross proxy (separate from logs), T2 on-call ~doubled, D3-D5 binlog/topology/RAW consistency, C2/C3 incident+acceleration cost, S5 30-day VMware-warm reverse off-ramp.

## Why: load-bearing for ploidy-paper evidence
- Same Deep×2/Fresh×2 protocol as prior arch-split, Redis-CDN, fluentql cases
- 0 CHALLENGE bidirectional + ~80% overlap + Fresh-unique decision-frame items = same recurring pattern
- Author's COI block (4 vectors declared) demonstrates that *disclosure is not mitigation* — load-bearing for paper claim that structural recusal beats reflective bias-correction

## How to apply
- If user revisits this migration: counter-proposal stable (re-sequence internal-tools-first, contract 2nd proxy author this month + freeze proxy scope, 6-month re-baseline, document pause-and-stabilize off-ramp, observability bridge before billing, decomposed cost model, specify decision-rights)
- If user runs another arch/migration debate: expect same severity-floor under-grading from Fresh — pre-flag consequence-chain items for HIGH minimum
- Calibration: stop iterating after Deep×2+Fresh×2+bidirectional cross — further rounds reproduce pattern without changing verdict
