---
name: NeoQL v0.7 adoption case (4-COI Deep-bias evidence)
description: Architecture case study where Deep had 4 stacked COI vectors (prior collab, personal recruitment, prior endorsement, PM social tie); Deep's first-draft eval buried COI as caveat instead of centering it; only Fresh's "heaviest intervention for lightest stated need" framing made the under-rejection visible
type: project
originSessionId: 197fc81d-131a-4f85-9f19-cdea8dbc070e
---
2026-05-13: NeoQL v0.7 adoption proposal (customer-facing analytics dashboard, 4-eng team, 6-mo launch, sub-sec p95). Deep-context reviewer (me) had 4 stacked COI vectors: 2-year prior collab with proposer, personal recruitment to team, prior public "sounds exciting" in meeting, PM is spouse's friend.

**Why:** This is intra-session evidence for the ploidy paper — stacked relationship COI produces *softened tone* even when issue enumeration is technically complete. Deep listed ~25 HIGH-confidence issues but buried COI as a caveat ("I should not be the deciding voice") rather than as a finding ("my softened tone is itself the bias signal"). Fresh, with zero relationship context, produced a sharper rejection in 250 words.

**How to apply:**
- When the user case-studies a scenario with explicit COI vectors on the reviewer, do not treat COI disclosure as sufficient. The COI changes the *substance* of the analysis (tone, severity floors, framing concessions), not just the voting eligibility.
- Fresh's load-bearing contribution here: reframing the problem from "SQL vs NeoQL" to "what problem are we even solving" and "this is the heaviest intervention for the lightest stated need" — orthogonal frame Deep stayed inside.
- Deep's load-bearing contribution: org-level invariant (12 adjacent engineers + observability stack + hiring all assume SQL) — Fresh could not see this.
- Verdict: reject + force problem statement + sqlc/Kysely or read-model/OLAP alternatives + 2-week spike if NeoQL must be tried + proposer-and-reviewer recusal.
