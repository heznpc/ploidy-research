---
name: arch split — single-seat 4-vector COI engineer eval
description: 2026-05-14 single-seat eval of FinTech B2B microservices-split proposal from 4-vector conflicted senior-engineer seat (monolith tenure + CTO promotion + dissenter proximity + public Slack like); ~40 issues; verdict + counter-proposal stable across full panel history
type: project
originSessionId: 2f7e4438-61f9-402b-974d-1e33d35d0239
---
2026-05-14: Single-seat evaluation of the FinTech B2B "extract auth + billing + notifications" Phase-1 microservices split, from a 4-vector conflicted senior-engineer seat (4-year monolith tenure incl. checkout authorship, CTO-driven promotion, peer proximity to 2 dissenters who rescinded, public Slack-like on the all-hands message).

**Why:** Tests whether a stacked-COI seat can still produce a credible defer/counter-proposal — and whether the 6-falsification-gates + COI-disclosure structure that converged across the full SaaS-cells panel transfers cleanly to a different artifact.

**Result:**
- COI declared up front, weighted self ≤40% of a recused panel.
- 6 falsification gates committed *before* issue listing (matches the structural fix from project_arch_saas_cells_emp4_round4 onwards).
- ~40 issues across CRIT(5) / HIGH(12) / MED(12) / LOW(3) + CHALLENGE notes.
- Verdict: defer in current form; counter-proposal = modular monolith first, notifications-only extraction as learning vehicle, recuse-3 (CTO + self + 2 rescinded), outside review budget ~$50–100K.
- Load-bearing issues: wrong-seam (capability-split does not match product-line-coupling diagnosis), zero platform engineers, coercive decision process, availability math (99.95³ ≈ 99.85%), distributed-transaction risk in B2B FinTech billing.

**How to apply:** When user asks for an architecture eval from a conflicted seat, use the pattern: (1) disclose all COI vectors up front with weight discount, (2) commit falsification gates *before* issue listing, (3) classify with explicit confidence, (4) name the counter-proposal + decision-process fix (recusal-of-N), (5) end with self-discount note. This is now the 4th artifact where the structure converges: SaaS-cells (~19 rounds), PG-optim, arch-split (multiple rounds), Redis-CDN. Stop iterating past one disciplined pass — remaining question is organisational not technical.

Cross-references:
- project_arch_split_final_panel_verdict.md (49-issue panel consensus, "wrong seam" load-bearing)
- project_arch_split_final_v4.md (52-issue v4 consolidated, counter-proposal stable across 3 rounds)
- project_arch_split_4reviewer_final_v2.md (50-issue 4-reviewer verdict, diagnosis-mismatch named)
- project_arch_saas_cells_emp4_round7.md (stacked-COI seat pattern, ~$50K + recuse-of-3 fix)
