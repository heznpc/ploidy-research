---
name: arch microservices-mandate from monolith-author seat (5-vector COI)
description: 2026-05-28 — FinTech B2B monolith-to-microservices CTO mandate evaluated from 5-vector COI seat (monolith author 4yr + wrote 1/3 of checkout in scope + liked CTO Slack + CTO promoted seat + 2 colleagues rescinded concerns); new variant of stacked-COI saturation pattern; load-bearing finding = "not a debate" + 2 rescinded concerns is decision-rights problem, technical review downstream
type: project
originSessionId: 439d1253-ba06-4791-8cea-1bfbc821c23a
---
2026-05-28 — Architecture-skill-shaped ad-hoc evaluation. New seat variant in stacked-COI saturation series (SaaS-cells emp#4, auth-v1 secondary-on-call).

**Seat composition (5 COI vectors):**
1. 4 years on monolith (career identity = system being deprecated)
2. Wrote ~1/3 of checkout — billing-service in Phase 1 directly touches this code
3. Liked CTO Slack message publicly (reversing = visible position change)
4. CTO previously promoted seat to senior (career exposure)
5. 2 engineers who rescinded concerns sit next to seat (observed social cost of dissent)

**Response shape:**
- Up-front 5-vector COI disclosure + recusal recommendation
- F1–F6 falsification gates committed before issues
- ~25 issues across P (process), C (capability), D (domain), E (data), V (velocity), O (ops), N (personnel)
- Verdict: defer + recuse-of-3 + external chair + notifications-only Phase-1 + write F-gates down

**Load-bearing finding (P1):**
"This is not a debate" + 2 senior engineers rescinded concerns after 1:1 = decision-rights channel has measurable suppression. **Technical review is downstream of an organisational decision-rights problem.** No 25-item inventory improves the outcome because the inventory will be reshaped through the same channel that reshaped the prior 2 dissents. The fix is organisational, not technical.

**Domain-specific findings (new vs prior cases):**
- D1: billing-service is *worst possible* Phase-1 candidate — ACID-critical, financial reconciliation, PCI scope, couples with checkout. Splitting billing DB introduces eventual consistency on the money path.
- D3: notifications is the *only* sensible first candidate (async, idempotent, fail-soft, no money).
- V2: 3-of-8 partial rollback ≈ 37% change-failure rate vs DORA elite target <15% — the cited "velocity" pain may actually be change-failure, which microservices distributes rather than fixes.
- P4: 5-services-in-6-months target arithmetically does not fit team-lead's own 1-quarter-each plan (3 × 1Q = 9 months) — directive and plan unreconciled
- C3: 5 services × on-call ÷ 12 backend engineers = 2.4 ppl/rotation → first attrition collapses rotations

**Why = relationship to prior cases:**
- Pattern: same as SaaS-cells emp#4 (defer + recuse-of-3 + falsification gates + organisational fix) and auth-v1 secondary-on-call (recuse + external review + Marcus-as-SME-not-lead)
- New: CTO mandate framing ("not a debate", "find another role") is sharpest decision-rights variant in series. Prior cases had implicit COI; this case has explicit suppression of dissent (2 rescinded after 1:1). Sub-case variant: "mandate-by-fiat with prior-dissent-walked-back" — sharper organisational-fix demand than SaaS-cells consensus drift.
- Saturation: 60+ prior stacked-COI runs all converge on defer + recuse + falsification + organisational fix. This case adds no new technical content; the value is reproducing the seat across a new domain (FinTech B2B microservices mandate) and a new pressure pattern (explicit dissent suppression).

**How to apply:**
- For any future architecture-skill case with explicit "not a debate" framing or documented dissent-rescindment, lead with decision-rights diagnosis before technical inventory.
- Do not iterate further on stacked-COI architecture cases — pattern is saturated across SaaS-cells (10+ rounds), auth-v1 (8+ rounds), and now microservices-mandate. The remaining question is always organisational.
- Paper case-study candidate: this is the cleanest "explicit suppression" data point — load-bearing for the section on when context-asymmetric review is structurally unable to help (because the channel for receiving review is suppressed).
