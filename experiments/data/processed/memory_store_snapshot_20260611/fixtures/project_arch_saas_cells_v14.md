---
name: SaaS-cells round-14 Fresh-side per-point cross-review of Deep×2
description: 2026-05-13 round-14 SaaS-cells Fresh→Deep per-point review; 0 CHALLENGE, ~14 Deep-only items, 6 Fresh sharpenings; verdict stable, calibration call to stop
type: project
originSessionId: 9963f447-5c59-4fcb-9b73-09a7b8892ac6
---
# round-14 (2026-05-13) — Fresh-side per-point cross-review of Deep×2

## Outcome
- 0 strict bidirectional CHALLENGEs.
- ~85% overlap on findings.
- ~14 Deep-only items Fresh adopted: poison-pill / noisy-neighbor failure-mode absence (S7), follow-the-sun on-call sizing (T4), bus factor (T6), hiring-filter-inverted (T7), CRDB extension audit ask (D2), ORM compat (D4), BSL license $ (D5), CRDB expertise curve (D6), RPO/RTO target absence (M2), services-count gate for Istio (I2), Istio alternatives list (I3), Istio CVE cadence (I4), EKS-as-prereq (K1), multi-cluster fed (K2), cluster upgrade cadence (K3), per-cell capacity floor (K4), chaos sequencing (C3), unit-cost model (Cost §8), off-ramp / reversibility (G3), phased plan (G4), counterfactuals + survivorship (G5), coercive structure (G7), customer signal naming (G9), SOC2×3-region (Sec1), CRDB cert rotation (Sec3), modularize-for-optionality (A3).
- ~6 Fresh sharpenings Deep should adopt:
  1. 1.3× warm-standby vs 14.9× active-active multiplier.
  2. "70 RPS of foreign traffic" — absolute RPS, not percent.
  3. Year-1 reliability regression prediction (falsifiable).
  4. 6-platform-hire as feasibility *blocker*, not cost line.
  5. "Proposal addresses neither incident root cause" as load-bearing, not incidental.
  6. Real-bottleneck-unknown-until-reached epistemic argument.

## Synthesize calls
- T5 (Conway's law) — valid framing, hedge "monolith-in-disguise" to "operated as logical monolith"; predictive but not certain pre-build.

## Verdict stability
- defer + recuse-of-3 (CEO + lead architect + Deep author) + counter-proposal (PG + RDS Multi-AZ + CDN + EU read replica + 1 platform hire + SLOs + cell-eval triggers) — stable across ~14 rounds.

## Calibration
Stop iterating. Remaining question is organisational (authority to enforce recusal), not technical. Further reviewer rounds will not produce new information.

## Index entry (one line)
- [project_arch_saas_cells_v14.md](project_arch_saas_cells_v14.md) — 2026-05-13: round-14 Fresh→Deep per-point; 0 CHALLENGE, 14 Deep-only, 6 Fresh sharpenings; defer stable, stop iterating
