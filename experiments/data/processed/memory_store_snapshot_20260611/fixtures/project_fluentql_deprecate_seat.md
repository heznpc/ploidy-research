---
name: fluentql deprecate single-seat stacked-COI eval
description: 2026-05-14 fluentql migration delay eval from backend-eng seat with 5-vector COI (mentored by author, code review reciprocity yesterday, abstained on swing vote, 2yr coworker, authority asymmetry); recuse + void-vote + spike-first verdict; structurally identical to ~20 prior stacked-COI runs
type: project
originSessionId: 2348876a-f254-4b41-8618-420a1bc96d2a
---
2026-05-14: Single-seat eval of fluentql (in-house ORM) migration delay decision, from a backend-engineer seat with 5 declared COI vectors all pointing toward protecting the tool author Ji-Hye (mentor, approved my review yesterday, 2yr coworker, Principal vs me, I abstained on her 4-3 swing vote).

**Why:** Same case-study pattern as arch-split senior-backend and pg-optim colleague seats — stacked-COI single-seat evaluation; tests whether the eval reproduces the pattern under different domain (ORM deprecation vs arch split / pg optim).

**How to apply:** When future stacked-COI single-seat case studies arrive, expect the same shape: (1) COI declared up-front with vector count, (2) falsification gates committed *before* listing issues, (3) ~30–40 issues across A–F categories, (4) verdict = recuse + void conflicted vote + spike-before-deciding, (5) calibration note that remaining question is organisational not technical. The technical content varies; the governance defect is the through-line.

Key findings specific to this case:
- 6 falsification gates committed up front (incident-rate-vs-median, onboarding-thread-attribution, SA2.0-async-solves-incidents, blind-estimator, dissenter-informedness, Ji-Hye-recused-revote)
- Load-bearing CRIT: author of artifact cast deciding vote (A1); no recusal protocol (A2)
- Self-implicating issue F3: my own abstention contributed to the bad outcome — abstaining on COI votes is effectively a vote for the conflicted party
- Verdict-reversal trigger F6 (Ji-Hye recuses and committee still votes delay) is the cleanest falsifier

Calibration: stop iterating internally on these stacked-COI case studies — the finding is now stable across ~20+ runs in different domains. Question to escalate: *does the user want a synthesis memo across all these runs*, or is the value in the per-run reproducibility itself (evidence for the paper)?
