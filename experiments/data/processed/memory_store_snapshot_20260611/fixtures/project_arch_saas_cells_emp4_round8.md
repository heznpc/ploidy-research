---
name: SaaS-cells employee-#4 single-seat round 8
description: 2026-05-14 ~19th-round single-seat SaaS-cells eval (same 4-vector stacked COI); ~45 issues A–J; falsification gates as withdrawal-conditions; defer + recuse-of-3 + ~$50K stable; calibration call to stop iterating
type: project
originSessionId: c6547fd1-b524-41d1-aac0-3116e052bc35
---
# SaaS cells round-8 (emp#4 stacked-COI seat) — 2026-05-14

## Context
- ~19th overall evaluation; ~8th from emp#4 single-seat 4-vector COI configuration.
- Same proposal: 200K-user Series-A B2B SaaS, 850 RPS, $94K/yr → proposed multi-region active-active + cells + Istio + CRDB + custom GLB + chaos = $1.4M infra + 6 FTE.
- Same stacked COI: report-to-CEO, co-authored cell diagram at retreat, signaled platform lead on approval, employee #4 seed-era tenure.

## Novel framing this round
- **Falsification gates phrased as withdrawal-conditions** ("I would withdraw my recommendation if...") — makes the recommendation pre-committed-falsifiable, defends against retroactive rationalisation. Six gates: sustained 5K RPS / signed residency contract / decomposed <$400K budget / 3+ availability incidents/quarter from single-region / 3+ contracted residency customers / written off-ramp <2 weeks.
- **D1 explicitly corrects proposal's "multi-master PG" framing** — CRDB is Raft-consensus, not multi-master; cross-region write p99 = 50–200ms, not 38ms. Proposal misstates its own DB choice.
- **C3 surfaces $1.4M omits 6-FTE payroll** — fully-loaded program cost = $2.6–3.2M/yr, not $1.4M.
- **C4 unit-cost-per-user calc** — $0.47/user/yr → $16/user/yr = 34× increase; destroys free-tier margin.
- **G6 names meta-bug** — no one at retreat raised COI, including reviewer; the structural problem is invisible to participants.

## Issues
~45 across A–J:
- A scale mismatch (4) — load-bearing
- B team mismatch (5) — load-bearing
- C cost / financial discipline (4) — load-bearing
- D technology selection (6) — incl. CRDB-correction, Istio cost, custom-GLB NIH, chaos NIH, cell-router unspecified
- E reliability paradox (4) — more systems = more incident surface; SLO undefined
- F migration / reversibility (4) — no off-ramp for CRDB → PG
- G governance (6) — 2-person retreat draft for $3M decision, recusal not raised
- H compliance (2) — multi-region creates GDPR/APPI scope, doesn't reduce it
- I opportunity cost (3) — 12–18mo product stall, hiring crowd-out
- J right-sized counter-proposal — PG replicas + CDN + managed services + SLO-first, ~$50K/yr, 0 new FTE, reversible

## Stable across 19 rounds
- Verdict: **defer**
- Recusal: CEO + lead architect + emp#4 (any retreat-attendee with material upside)
- Counter-proposal cost envelope: ~$50K/yr incremental
- 0 strict CHALLENGE bidirectional; ~80–85% catch overlap

## Calibration
- Technical answer has been the same for 19 rounds, 0 strict CHALLENGEs.
- Remaining question is **organisational, not technical**: how does someone reporting to the CEO + co-author of the proposal credibly deliver "defer + you should recuse" upward?
- Further technical iteration adds no information. Next move is process design (e.g., outside-advisor decision authority, written RFC with falsification gates, named recusal list), not more architecture review.
- **Recommendation: stop iterating on this case study.**

## Connects to
- All `project_arch_saas_cells_*` entries (rounds 1–18, multiple seat configurations).
- `feedback_deep_reading.md` — proposal + numbers fully read before issues listed.
- `project_session_evidence.md` — evidence that repeated single-seat evaluations of a converged case produce no new technical content; useful as a Ploidy-paper negative-result data point.
