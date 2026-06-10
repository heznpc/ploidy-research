---
name: NeoQL adoption Deep×2→Fresh×2 cross-review
description: 2026-05-13 NeoQL-adoption proposal Deep response to Fresh×2; 0 strict CHALLENGE bidirectional, 2 severity-floor SYNTHESIZE, ~85% overlap, 10 Deep-only items concentrated in COI/process/security/compliance
type: project
originSessionId: 1fa96654-17d1-40ef-93ae-bb7c2b4f2c34
---
2026-05-13. NeoQL adoption proposal (v0.7 query language, customer-facing analytics, 6-month launch, sub-second p95, 5-table joins + recursive CTEs + window aggs). Deep seat declared 4 COI vectors up front (prior collab, personal recruitment, "sounds exciting" soft-commit, PM spouse-tie).

**Cross-review pattern:** 0 strict CHALLENGEs bidirectional. ~85% catch overlap. Fresh reached the same Reject verdict with zero context.

**Severity-floor SYNTHESIZE (Fresh under-graded):**
- F1-12 "When NeoQL takes off" base-rate: MED → HIGH (v0.7 OSS DSL survival rate too low to grade MED)
- F2-15 personal-relationship-as-vendor: LOW/MED → HIGH (single point of contact *is* the SLA on a customer-facing product)

**Fresh framings adopted (sharper than Deep originals):** "incident MTTR externalised company-wide," "customer-facing analytics *is* the scale case," "structural mismatch not tuning problem," "language bugs and product bugs become indistinguishable," "tutorial knowledge not production operational knowledge (which doesn't exist yet)," "translation problem during the worst possible moment," "rewriting every query on migration off," "not a single requirement NeoQL satisfies better than SQL."

**Deep-only items (require org context, not derivable from brief):**
1. Proposer-as-decider COI on the lead (proposer + owner + credit-recipient cannot be deciding vote)
2. "Sounds exciting" room-anchoring effect from a reviewer's prior public soft-commit
3. Recusal recommendation as decision-process fix (Fresh got outcome right but missed process repair)
4. Rust expertise gap for debugging the compiler itself
5. Hiring tax / internal mobility block on a 4-person team with a niche language
6. License risk on v0.7 (RSAL/SSPL/BUSL relicense pattern in pre-1.0 OSS)
7. SOC2 / customer-audit compliance story harder for "maintained by 3 people"
8. Security review absent (SQL-injection-class risk on multi-tenant + unaudited compiler)
9. Plan caching / prepared statements undocumented (bears on p95 target)
10. No budget for the failure scenario (3mo contractor + 1wk onsite; nothing for fork/rewrite)

**Verdict stable: Reject as proposed.** Process fix = recuse lead + PM + Deep seat, 2-week spike on representative workload with falsification criteria stated *before* spike, comparison set = parameterized SQL baseline + Malloy + PRQL + sqlc, default to not-adopt if no consensus.

**Meta-finding:** COI didn't change Deep's catches, it changed Deep's *tone*. First-draft Deep buried recusal as voting caveat instead of substantive bias signal; Fresh's flatter rejection was the more reliable verdict. This is the ploidy phenomenon — context-asymmetric debate surfaces what stacked-COI Deep softens.

How to apply: when the proposal-evaluator has multiple COI vectors (relationship + prior commitment + relational tie), require a Fresh cross-check before voting. The Deep evaluation is useful for org-process catches (COI, recusal, anchoring) but unreliable for *tone calibration* on the verdict.
