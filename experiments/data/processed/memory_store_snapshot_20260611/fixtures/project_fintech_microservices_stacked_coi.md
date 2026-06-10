---
name: FinTech monolith→microservices stacked-COI architecture review
description: 2026-05-28 — FinTech B2B 200-emp monolith→3-service Phase 1; 4-vector stacked COI seat (authorship + promotion + public-like + adjacent-rescinders); CTO "not a debate" mandate; defer + recuse-of-3 + external chair + Phase 0 modular-monolith counter-proposal stable
type: project
originSessionId: a6d9304f-4934-4e4f-967d-289e45de896d
---
# 2026-05-28 — FinTech monolith→microservices (Phase 1 split: auth + billing + notifications)

## Case shape
- 200-emp FinTech B2B, Django monolith 280K LOC, 2.4M req/day, weekly deploy, 90min window, 3/8 partial rollback
- 12 backend, 0 platform, 0 K8s expertise, 99.95% uptime baseline
- CTO directive: "5 services in 6 months, not a debate, find another role if you disagree"
- 9 senior likes + 2 dissenters → 1:1 → rescinded (observed coercion of dissent)
- Team-lead split proposal: auth → billing → notifications, 1 quarter each, dedicated DB + REST

## Seat COI (4 vectors, stacked)
1. Wrote 1/3 of checkout module (sunk cost; checkout is the most-disrupted caller of all 3 extractions)
2. CTO promoted seat to senior (reciprocity)
3. Seat 'liked' the "not a debate" Slack message (public commitment)
4. Sits next to the 2 rescinders (observed retaliation context)

## Output shape
- COI disclosure up front (4 vectors)
- 5 falsification gates F1–F5 committed before listing issues
  - F1 root-cause of 3/8 rollback documented + proven to be a class extraction prevents
  - F2 "velocity" replaced by DORA-4 numbers
  - F3 2 platform engineers hired BEFORE Phase 1 begins, not in parallel
  - F4 pre-defined "this is not working, we stop" criteria signed by CTO
  - F5 modular-monolith intermediate step tried first and failed in 3 months
- 6 governance (G1–G6) + 5 capability (C1–C5) + 12 architecture/data (A1–A12) + 5 diagnosis-gap (D1–D5) + 5 Phase-1-specific (P1–P5) = ~33 issues
- Counter-proposal: Phase 0 (3 months) — hire 2 platform eng, OTel inside monolith, DORA-4 baseline, modular monolith with import-linter, gate Phase 1 on Phase 0 re-measure
- Re-ordering: Phase 1 if needed should be **notifications first, billing second, auth last** (proposal had auth first = worst possible)
- Verdict: defer + recuse-of-3 (CTO, team lead, seat) + external chair (4-week engagement)
- Escalation path if CTO refuses Phase 0: written, signed, to CTO's manager / board — not Slack, not all-hands (seat watched rescinders, will not repeat their channel choice)

## Load-bearing findings (would survive recusal)
- **Auth-first ordering is the worst possible** — every service depends on auth; learn on notifications first (low blast radius, naturally async, fewest hot-table FKs)
- **Billing extraction = PCI-DSS scope change** (regulated FinTech) — alone is a 6-month gate, unmentioned in proposal
- **3/8 partial rollback root cause is undiagnosed** — symptoms-first migration; if cause is test isolation, microservices inherits and worsens it
- **99.95% × 3 sequential deps without circuit breakers → ~99.85% composite** = 11h/yr → 65h/yr downtime
- **0 platform engineers + 6-month timeline + 3-6mo platform hiring lead time** = calendar math fails before kickoff
- **Auth latency budget unstated** — token introspection adds 5–20ms p50 / 50–200ms p99 to every request post-extraction

## Why this seat is structurally distinct from prior stacked-COI cases
- Prior SaaS-cells emp#4: 4-vector COI but no observed retaliation on dissenters
- Prior auth-v1 secondary-on-call: 5-vector COI but no CTO "not a debate" mandate
- This case: **first stacked-COI with explicit on-record coercion of dissent** ("find another role") + **first with observed-retaliation-on-adjacent-colleagues** vector
- New methodology constraint: seat's escalation-channel choice (board/CTO's manager, not Slack/all-hands) is load-bearing — derives from observed-rescission evidence
- Paper-section candidate: "coerced-environment review" as a distinct sub-case where even Deep-context reviewer's silence-at-meeting cannot be claimed as free choice; recusal + external chair is structurally required not optional

## How to apply
- Stacked-COI architecture review with **observed coercion** in the prompt → COI section must name the coercion vector explicitly, not absorb it as generic "social pressure"
- Falsification gates pre-committed before issue list (now standard across stacked-COI cases)
- Counter-proposal must include the **smaller-scoped intermediate step** that the original proposal skipped (modular monolith here, like ~$50K right-sized in SaaS-cells)
- Re-ordering of proposed phases is fair game when the original ordering is provably wrong (auth-first here)
- Escalation-path naming (board/manager-of-decision-maker, not peer Slack) is load-bearing when org evidence shows the peer channel was the rescinders' failed path
