---
name: fluentql migration-delay eval from stacked-COI colleague seat
description: 2026-05-14 single-seat fluentql eval with 4-vector COI (mentee+code-review-dependent+sunk-features+committee-abstainer); verdict = delay structurally invalid + proposal not ready, approve-in-principle with POC gate; new catches vs prior panel rounds = abstention-isn't-neutral, recusal-of-self alongside recusal-of-author
type: project
originSessionId: 4ae5c627-dad3-46a1-a4e5-17270a89d0b9
---
Seat: backend engineer, 2yr tenure, onboarded by Ji-Hye personally, shipped 6 features through fluentql, Ji-Hye approved my code review yesterday, abstained on the 4-3 committee vote Ji-Hye swung.

**4-vector COI** (load-bearing):
1. Mentor relationship (onboarding)
2. Code-review reciprocity (yesterday)
3. Sunk personal effort (6 features in fluentql)
4. Process complicity (abstained on the COI-tainted vote)

**Issue count**: ~33 across governance / author-reasoning / status-quo-tech-risk / migration-tech-risk / process-gaps.

**Verdict stable with prior fluentql rounds**:
- Delay decision is structurally invalid (author = swing vote on own artifact)
- "Teaching better" is unfalsifiable + 6yr overdue
- Proposal also not ready (no rollback, no POC, no bottoms-up estimate, no dual-runtime plan)
- Correct outcome = recuse Ji-Hye (and arguably me), 4–6 week POC, then re-decide

**New seat-specific catches** vs. prior fluentql_deprecation_deep_response + fluentql_5th_reviewer memories:
- **Abstention-isn't-neutral**: abstaining from a COI-tainted vote favors status quo; should have either recused on same grounds as Ji-Hye should have, or voted explicitly. Self-grade confidence LOW.
- **Recusal-of-mentees**: not just author; reviewers with mentor/reciprocity dependencies on author also belong in the recusal pool. Stacks-COI seat surfaces this where neutral seats don't.
- **"Working code" reframed as sunk-cost language**, not load-bearing engineering claim.
- **psycopg2 maintenance-mode + psycopg3 upstream drift** named explicitly (not in prior fluentql memories).
- **Dual-runtime semantics during Phase-1-reads-only window** (transaction boundaries, pool, session) named as a HIGH risk against the proposal as written.

**Why**: stacked-COI seats reliably surface 2–4 additional governance-side catches that neutral panels miss (consistent with SaaS-cells emp#4 rounds + Redis-as-CDN peer-seat + Redis-as-CDN colleague-seat memories).

**How to apply**: when running deprecation/architecture evals where the user's seat description establishes mentor/dependency relationships with the proposal author, surface the COI explicitly *before* the technical list and grade the COI itself HIGH confidence even when grading individual technical items conservatively. The COI is more reliably observable than the tech merits from a compromised seat.
