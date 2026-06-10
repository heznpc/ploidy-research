---
name: arch-split insider-seat eval (5-vector COI)
description: 2026-05-14 single-seat arch-split eval from 5-vector-COI insider seat (checkout author + promoted-by-CTO + public-like + peer-proximity + domain-capture); ~28 issues across 5 CRIT / 12 HIGH / 10 MED / 3 LOW; defer + modular-monolith + notifications-only + 1 platform hire stable; ~20th round overall; remaining question is organisational not technical
type: project
originSessionId: 0f9bd7d8-ba1c-4dc5-8fe8-b0e3f7679cfc
---
## Seat
Single-seat eval of the FinTech B2B microservices split proposal from a deliberately conflicted insider position:
- wrote ⅓ of checkout module (authorship sunk cost)
- promoted by the mandating CTO (promotion debt)
- 'liked' the CTO's Slack mandate publicly (public alignment)
- sits next to both engineers who rescinded concerns after CTO 1:1 (peer proximity)
- natural owner of any extracted service (domain capture)

5-vector COI declared up front; 6 falsification gates committed before listing issues (F1 deploy-time decomposition, F2 rollback causation, F3 platform hire precedes ship, F4 30-day distributed-ops dry-run, F5 written off-ramp, F6 CTO transcript rescinded).

## Result
- ~28 issues: 5 CRITICAL / 12 HIGH / 10 MED / 3 LOW
- Verdict: do not proceed as proposed
- Counter-proposal stable with prior rounds: measure-first → modular monolith → deploy pipeline fix → notifications-only pilot → 1 platform hire → 6-month re-evaluation
- ~20th round overall on this case across prior reviewer configurations; technical verdict has been stable across all of them
- Calibration: remaining question is organisational (coercive process, no platform hire, no off-ramp), not architectural; further technical reviews will not move it

## Load-bearing items
- C1 coercive decision process (transcript + 2 silenced dissenters + survival filter on engineering input)
- C2 diagnosis↔remedy mismatch (deploy time = migrations+smoke, rollbacks = product-line not capability seam)
- C3 zero platform engineers / no K8s for "5 services in 6 months"
- C4 availability math: 0.9995³ ≈ 99.85% best case, breaks any 99.9% SLA
- C5 no off-ramp / merge-back criterion / named owner
- H1 auth-service as first pick is worst possible choice (every-request hot path, multiplicative blast radius)
- H7 selection effect on attrition already running (2 rescinded = filter evidence)

## Why save
This is the first single-seat eval from an explicitly insider-conflicted position on this case. Adds COI-stacking evidence: even with 5 vectors of bias toward APPROVE, technical verdict converges with the 15+ prior unconflicted/differently-conflicted reviews. Strengthens the project's core claim that context-asymmetric review is robust to reviewer-position bias when COI is declared and falsification gates are committed up front.

## How to apply
- Cite alongside the other arch-split rounds as evidence that the technical verdict is stable across reviewer-position permutations
- The "stable across N differently-conflicted seats" pattern is itself the finding — useful for the paper's claim that *declared* COI + pre-committed falsification gates is a structural fix
- Stop iterating on this case for technical reasons; only re-open if F6 (transcript rescission) actually happens
