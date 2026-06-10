---
name: Redis-as-CDN insider-seat single-reviewer eval
description: 2026-05-14 single-seat Redis-as-CDN review from 4-year insider (promotion-committee tie to proposer + hired by approving EM + 6yr Redis user); verdict stable
type: project
originSessionId: e65084c0-5ca5-4cef-9d4b-95af5d598971
---
2026-05-14: ~Nth round of the Redis-as-CDN case study. New seat: 4-year backend engineer next to proposer; proposer was on reviewer's promotion committee; approving EM hired reviewer; reviewer has used the Redis-for-session/queue stack in prod for 4 of its 6 years (sunk-cost vector).

Output:
- Verdict stable: REJECT.
- COI disclosed up front + recusal recommended for proposer + EM + this seat.
- Load-bearing items unchanged across rounds: NIC ceiling, working-set > RAM, browser-L1 immutable URLs as the actual lever, geography (LATAM+APAC abandoned), cellular RTT, egress-doesn't-disappear, no decomposed bill, no architecture review, promotion-incentive alignment, no falsification criteria.
- Premise refutation (320KB avg / 1.8MB P90 vs Lead's "<50KB") graded HIGH and called out explicitly.
- Counter-proposal stable: decompose bill → immutable URLs → AVIF/srcset → multi-CDN → Origin Shield → re-measure.

**Why:** Tests whether stacked COI (reciprocal promotion + supervisory + sunk-cost on the same stack being extended) bends the verdict. It did not.

**How to apply:** When this case study is run again, expect the same axes to be load-bearing. If a future seat produces a DIFFERENT verdict under heavier COI, that is a finding worth noting; if the verdict stays REJECT, marginal value of another round is low — calibration call to stop iterating, the remaining question is organisational (who can run an unconflicted vote), not technical.
