---
name: redis_cdn_peer_seat_eval
description: Redis-as-CDN eval from in-team peer seat (proposer was on my promotion committee, EM hired me, 4y Redis user) — COI-stacked review reproduces REJECT verdict
type: project
originSessionId: d1412ebe-68a7-4862-874e-222c0d982281
---
2026-05-14: Redis-as-CDN proposal evaluated from a stacked-COI peer seat (4y collaborator, proposer on my promotion committee, EM is my hiring manager, 4y Redis production user).

**Why:** COI calibration — does the verdict hold from the seat with the strongest social pressure to approve? Prior 11+ rounds of Deep×2/Fresh×2 reviews all converged REJECT; this run tests whether a peer-seat single-reviewer call independently lands the same way.

**How to apply:**
- Verdict **REJECT** reproduced; ~45 issues across 8 categories (premise refutation, capacity/physics, protocol mismatch, geography, cost, free levers, ops, compliance, governance).
- Load-bearing technical chain stable: A1 premise self-refute + A2 working-set/RAM mismatch + A3 egress economics inverted (~7–9× cost increase) + B1 NIC ceiling + C1 Redis≠HTTP + D1 POP coverage.
- New emphasis from this seat: **H5 rhetorical pre-emption of dissent** ("anyone proposing CDN-only is missing the principle") explicitly named as raising social cost of disagreement — this is the COI-seat-specific catch that anonymous reviews underweight.
- Falsification criteria declared up-front (4 measurable conditions); proposal provides zero of them.
- Counter-proposal stable: decompose bill → CDN contract renegotiation → immutable URLs + Origin Shield → scoped POC only if gap remains.
- Recusal requirement reproduced: proposer + EM + tightly-reporting peers (including this seat) recused; neutral ARB chair.

**Calibration call:** stop iterating on Redis-as-CDN. Verdict converges across Deep×2, Fresh×2, 5th-reviewer, and now peer-seat single-reviewer — remaining question is organisational (will the approval chain actually recuse), not technical.
