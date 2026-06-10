---
name: arch_logistics_migration_4session_synthesis
description: 2026-05-14 4-session full-context synthesis of logistics on-prem→EKS migration from platform-eng 5-vector COI seat; 4 CRIT / 22 HIGH / 9 MED / 1 LOW; defer + reverse-sequence + recuse-of-3 + ~$30–60K hybrid hardening unanimous 4/4
type: project
originSessionId: d9a051ed-8ba4-4823-9d1e-3bfe35ea126e
---
4-session full-context synthesis, logistics on-prem→EKS migration, platform-eng 5-vector COI seat (proxy author + 6mo team + leaving peer + nodded at CTO + identity-coded codebase). ~14th stacked-COI case overall.

**Verdict**: defer push-forward proposal as written. 4/4 unanimous, 0 CHALLENGE bidirectional.

**Issue counts**: 4 CRITICAL / 22 HIGH / 9 MEDIUM / 1 LOW (= 36 confirmed). All HIGH and CRIT items unanimous 4/4.

**Load-bearing CRITs**:
- No rollback / abort criteria (billing = $2.4M/day one-shot/night)
- Billing-first inverts risk ordering (most expensive, least reversible used as first-of-class)
- No stop-and-stabilize trigger defined
- Coercive process — CTO all-hands + proposal w/o fallback ⇒ recuse-of-3 (proxy author, team lead, leaving peer) load-bearing

**Falsification gates F1–F6** committed before issues across all sessions. Current status: all 6 unverified; ≥4 visibly failing → by seat's own rule, defer is correct.

**Counter-proposal (stable across all 4 sessions and prior runs)**:
1. Reverse sequence — internal tools → portal write-path → GPS/fleet → billing/route-opt last (with full dual-run + documented rollback)
2. Stabilize hybrid first — proxy HA, unified observability, secret rotation (~$30–60K + 4–8 weeks)
3. Fund proxy-author KT explicitly before Q4
4. Recuse-of-3 from final decision; route outside CTO reporting line
5. Per-service rollback plan with named DRI, abort criteria, cost-of-abort
6. Re-baseline timeline against F1–F6

**Calibration**: stop iterating internally — pattern stable across ~14 stacked-COI cases now. Remaining question is organisational (external channel to CTO), not technical.

**How to apply**: when this migration / similar push-forward-under-CTO-framing comes up, do not re-litigate technical merits; surface the organisational-channel question. The defer + reverse-sequence + recuse-of-3 + hybrid-hardening verdict is the stable finding.
