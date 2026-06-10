---
name: arch saas-cells 4-session synthesis
description: 2026-05-14 4-session SaaS-cells full-context synthesis — ~40 issues (3 CRIT/28 HIGH/9 MED); 14 unanimous; defer + recuse-of-3 + ~$30–60K counter-proposal stable
type: project
originSessionId: 0a8e4480-1fe7-4b3f-9ddf-d975497a7788
---
# 4-session SaaS-cells synthesis — 2026-05-14

Combined 4 independent full-context evaluations (employee #4, 5-vector COI seat) of the weekend-drafted SaaS cells / CRDB / Istio / 3-region active-active proposal.

## Verdict (4/4 unanimous)
DEFER. None of F1–F6 falsification gates fire. Counter-proposal: ~$30–60K/yr (eu-west read replica + CDN + 1 platform hire + kill criteria).

## Severity totals
- **CRITICAL: 3** — F1 custom-GLB build-vs-buy (Route53+ALB+GA exists), I1 weekend-draft process artefact, I2 COI recusal (CEO + lead architect + emp#4).
- **HIGH: ~28**
- **MEDIUM: ~9**
- **Total: ~40 confirmed issues**

## 14 unanimous (4/4) load-bearing items
A1 (850 RPS, 10× PG headroom), A2 (15× infra spend for 6× headroom), A3 (CRDB p99 regresses 38→50–200ms), A4 (<8% non-US solved by replica+CDN), B3 (6 FTEs = 33–50% of eng), C1 (1 plat-eng for 24 mesh planes, 3–4× understaffed), C3 (hiring 6 plat-eng unproven), E2 (routing/provisioning/rebalance/obs unbuilt + unscoped, 12+ mo), G2 (no signed residency contract — speculative compliance), H1 (2 incidents = deploy bug + 3rd-party, cells solve neither), I1 (weekend draft, no RFC, no cost model, no rollback, no off-ramp), I2 (recuse 3 COI authors), I3 (no falsification criteria in proposal), I5 (in-group channel broken — reviewer being emp#4 is the evidence).

Concentration: diagnosis mismatch + process governance + scale-cost mismatch.

## Calibration
~22–24th round overall. Verdict has been stable across all stacked-COI seats and full-context panels. F1–F6 gates have not flipped in any round. **Remaining question is organisational, not technical**: how a "no" reaches the board without CEO filtering. Internal iteration past this is process theatre.

## Load-bearing structural fix
- Recuse 3 authors (CEO + lead architect + emp#4 / signalled platform lead).
- External SRE review (~$15K, 1 week, named consultant) before any commitment.
- If external concurs → board directly. If not → reviewer has miscalibrated and should update.
