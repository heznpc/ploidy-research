---
name: arch_3region_5th_reviewer
description: 5th-reviewer Fresh pass on 3-region cell-based arch proposal Deep×2; 0 strict CHALLENGE, 4 severity-floor escalations; 11 Fresh-side gaps incl. SLA/customer-residency, no-named-DRI, what-if-no-vote-body, founder-departure soft-power
type: project
originSessionId: f7d6fb5b-c555-4a52-ba85-953a84f0d2a5
---
2026-05-08: 5th-reviewer Fresh pass on Deep×2 arch review (3-region × 8-cell × CockroachDB × Istio × custom GLB proposal at Series-A B2B SaaS, 200K users, 850 RPS peak, 1 platform eng / 1 sec eng).

**Why:** Both Deep authors had declared COIs (one was retreat co-author, one was promised platform-lead role). Even with COIs declared and severity-floor-grading-against-self, a Fresh cross-check is required to verify they didn't under-grade in subtle ways or miss Fresh-only catches.

**How to apply:** When a Deep author declares COI and grades against their own interest, validate by Fresh cross-check rather than trusting the self-correction. Common under-gradings even in COI-aware Deep: governance items (recusal protocol, board sign-off), runway/financial items, product-velocity opportunity cost, and migration-plan absence.

**Result:**
- 0 strict CHALLENGEs across all Deep points (P1–M6, R1–R9, $1–$6, I1–I6, T1–T6, etc.)
- 4 severity-floor escalations: P8 (no SLOs), R2 (3 undeclared COIs), $5 (runway), T2 (product velocity → 0), D4 (no migration plan), R9 (no CFO sign-off) — all should be CRITICAL not HIGH
- 11 Fresh-side gaps:
  1. Cost figure $3.2M likely under-stated → $4–5M true Y1 (egress unbroken-out)
  2. us-east-1 outage history under-weighted (warm DR is the 5% of the proposal that's defensible)
  3. "Punching above our weight" is a cultural/identity defect not just reasoning
  4. Lead architect's COI > employee #4's (equity/tenure/recruiting power not differentiated)
  5. Founder-departure soft-power dynamic when CEO-authored proposal is rejected
  6. Cockroach managed-vs-self-hosted unaddressed; proposal benefits from ambiguity
  7. "Re-vote recused" assumes a vote body that may not exist at Series-A
  8. Customer-visible enterprise SLA / data-residency contracts not mentioned (could legitimately drive eu region — or their absence is diagnostic)
  9. Migration risk *to customers* (churn during 12–24mo more-incidents window)
  10. No named DRI per system — five systems, all "we will hire"
  11. No "what happens if we don't do this" failure-mode-of-status-quo section

**Verdict alignment:** Both Deeps' verdicts (REJECT as packaged, recuse authors, staged counter-proposal: SLOs → observability → Aurora → eu read-replica → revisit at 5K RPS) are stable and not over-stated. Fresh adds: establish arch-decision body if none exists; verify enterprise-contract constraints; differentiate author COI weights.
