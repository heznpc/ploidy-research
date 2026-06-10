---
name: arch-split senior-backend stacked-COI seat round 2
description: 2026-05-14 — 2nd run of senior-backend 5-vector COI seat on Phase-1 microservices split; ~30 issues A–H + F1–F6 gates + recuse-of-5 + ~$30–60K counter; ~21st overall round; verdict stable; calibration call stop iterating
type: project
originSessionId: f5539568-fc95-485e-b5ce-b2403d393857
---
2nd run of senior-backend stacked-COI seat (4yr monolith + wrote checkout + liked CTO Slack + sits next to rescinders + CTO-promoted). ~21st round overall on this case.

Output shape unchanged from r1:
1. 5-vector COI declared up front (added domain-capture on checkout/auth as 5th vector this round).
2. F1–F6 falsification gates committed before issues (F1 platform team ≥3, F2 <10 cross-FK paths, F3 written rollback criterion, F4 RCA on 3/8 rollbacks, F5 ≥2 sign-offs without 1:1, F6 99.95% includes deploy windows).
3. ~30 issues across A–H, COI-aligned items explicitly flagged (A1 product-line wrong-seam still load-bearing, C1 auth-first worst pick, G1 poisoned dissent + G4 pre-filtered reviewer pool both flagged COI-aligned since I'm in the 'liked' group).
4. Counter-proposal: recuse 5 (CTO + team lead + 2 rescinders + me), $30–60K external review, F1–F6 in charter, notifications-only if extraction happens, platform hiring gate-zero.

Load-bearing across both runs of this seat:
- A1 diagnosis mismatch (deploy latency + product-coupling ≠ horizontal extraction)
- A3 wrong seam (product-line not horizontal infra)
- A4 99.85% composite < 99.95% monolith
- B1/B2 0 platform engineers + on-call explosion
- C1 auth-first = highest-coupling-first (worst pick)
- G1 + G4 coercive process + pre-filtered reviewer pool (COI-aligned for me)
- H1 missing RCA on 3/8 partial rollbacks = most likely the actual root cause is migration sequencing, which microservices worsen

Why: 21+ rounds, no verdict movement, no new technical surface from changing the seat.

How to apply: do not run a 22nd round. Future arch-split work should pivot to the organisational question (can this org execute a decision where the CTO is wrong?) or to a different case entirely. The process is now generating evidence about itself, not the architecture.
