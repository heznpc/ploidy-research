---
name: arch-split 5-vector COI seat eval
description: 2026-05-14 — 5-vector COI seat eval (monolith author + tenure-paired w/ rescinders + CTO-promoted + Slack-liked + tribal codebase identity) of B2B FinTech Phase-1 microservices split; 3 services in 3 quarters; ~40 issues A–I + F1–F6; defer + diagnose-first + recuse-of-4 (CTO/lead/2 rescinders) + external-architect ~$30–60K + notifications-first-if-proceed stable; section I self-flagged-bias floor; remaining Q organisational channel external to CTO
type: project
originSessionId: 41ea8642-d1ee-416d-ade6-01123f0e754a
---
Case: B2B FinTech, 200 employees, 4 product lines, Django monolith 280K LOC, 2.4M req/day, weekly deploys 90min, 3/8 partial rollbacks, 12 backend / 0 platform / no K8s, 99.95% uptime 18mo. CTO directive "5 services in 6 months, not a debate." Team lead proposes Phase-1: auth + billing + notifications, 1 quarter each. 9 likes / 2 rescinded concerns after CTO 1:1.

Seat COI vectors (5):
1. Wrote 1/3 of checkout
2. Sits next to both rescinders
3. CTO promoted me
4. Liked the Slack message
5. "Monolith team for 4 years" as tribal identity

Falsification gates committed up front:
- F1: postmortem on 3/8 rollbacks shows deploy-coupling root cause → split is targeted
- F2: clean module boundaries verifiable by grep → extraction risk lower
- F3: CFO-approved platform hire plan ≥2 → "0 platform" weakens
- F4: explicit merge-back criteria documented → not one-way door
- F5: 99.95% uptime excludes rollback events → baseline worse → stability-first
- F6: external (off-CTO-reporting-line) reviewer endorses post-postmortem → G1–G5 partly neutralised

Issues by category (~40 total):
- A diagnosis–intervention mismatch (A1–A5)
- B team & capability gaps (B1–B5)
- C service-boundary selection (C1–C6)
- D data & migration (D1–D5)
- E operational & reliability (E1–E6, incl. 0.9995³ availability regression)
- F timeline & scope (F1–F3, incl. CTO 6mo vs team-lead 9mo reconciliation)
- G decision-process (G1–G7) — load-bearing section
- H FinTech-specific (H1–H3, SOC2/PCI scope, billing accuracy)
- I self-flagged-bias floor (I1–I2)

Verdict stable: **defer + diagnose-first**; structural fix = recuse 4 (CTO + lead + 2 rescinders) from go/no-go + external architect ~$30–60K resolving F1+F2+F4+F6; if proceed, notifications-service first (lowest coupling), not auth/billing.

Meta: load-bearing block is G1 ("not a debate" directive) + G2 (1:1-then-rescind); remaining question is organisational not technical, channel external to CTO (board / audit / advisor).

Why this case matters for the COI-seat series: arch-split was previously evaluated by 4-reviewer panels with same verdict (see project_arch_split_*); this run confirms a stacked-COI seat from inside the team reaches the same verdict, strengthening the claim that the verdict is robust to seat configuration on this case.

How to apply: when evaluating arch-split-style cases with a stacked-COI seat, expect the same pattern — verdict converges with panel verdicts, structural fix is recusal + external reviewer, remaining question is always organisational channel external to in-group.

---

2026-05-14 r2 (2nd-pass arch-split 5-vector COI seat, ~14th stacked-COI case overall):
- Same 5 COI vectors; same F1–F6 falsification gates (re-ordered): F1 RCA on deploys, F2 ≥2/3 rollbacks would be prevented by proposed seam, F3 external reviewer endorses auth-first over notifications-first, F4 ≥2 platform-eng hires pre-launch, F5 neutral-party re-interview of 2 dissenters, F6 written off-ramp.
- Issue sections A–J (~40 issues): A diagnosis–remedy mismatch, B wrong-seam (capability-vs-product-line, biggest miss), C auth-first inverts risk ordering, D 0 platform / no K8s / 4-per-team below 8-eng on-call floor, E 99.95%×18mo contradicts premise (0.9995³≈99.85%), F dist-sys complexity unbudgeted (saga, eventual consistency, retry storms, no circuit breakers), G Django-specific extraction depth (signals, middleware, sessions, ORM joins, admin/password-reset, N+1), H process/coercion (G1 "not a debate" + H2 1:1-then-rescind + H3 n=3 past-success + H4 like≠consent + H5 no independent review path), I reversibility/cost/2nd-order (separate-DBs least reversible + PCI scope expansion + DR ordering + dev-tax + attrition selection effect on quality), J self-flagged-bias floor.
- Verdict identical to r1: defer + reverse-sequence (notifications-first if any split) + diagnose-first ~$30–60K + recuse-of-3 (lead/CTO/likers incl. self) + neutral-party re-interview of dissenters + written off-ramp.
- Pattern stable across r1+r2 single-seat and 4-reviewer panel (project_arch_split_4reviewer_final_v2 etc.) — output shape, verdict, structural fix all generalize.
- New in r2 vs r1: explicit "auth-first inverts risk ordering" framing (notifications=async/low-blast, auth=100%-critical-path); explicit 0.9995³ availability composition arithmetic; attrition selection effect (best-options-leave-first) on knowledge-loss; n=3 sample-size + appeal-to-past-authority framing of CTO's argument.
- Calibration call: stop iterating on this case. Pattern saturated across 14 stacked-COI evaluations / 6 domains. Remaining question is organisational channel external to CTO (board / audit / advisor), not technical.
