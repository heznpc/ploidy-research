---
name: Ploidy protocol — artifact injection requirement
description: Review-style Ploidy skills (/architecture, /review-pr, /spike, etc.) must inject the artifact-under-review into the Fresh seat, or Fresh degenerates into a refusal-to-fabricate response and convergence becomes impossible.
type: project
originSessionId: d2507c0a-5034-40e8-8b89-3476ca211ca8
---
Observed 2026-05-01 in an /architecture debate on a PG-only optimization plan: Deep produced a full architecture review (plan was in project context); Fresh correctly refused to review nothing, because the harness did not pass the plan text into the zero-context seat.

**Why:** Context asymmetry must be on *surrounding context* (history, decisions, team, memory), not on the *target artifact*. If both are withheld from Fresh, the debate has no shared referent.

**How to apply:** When reviewing or extending review-style skills (architecture, review-pr, spike, deprecate, post-mortem, product-decision), verify the skill template requires the artifact text as an explicit argument and injects it verbatim into the Fresh prompt. The Fresh seat should see: (artifact) + (review instructions) + (no project context). The Deep seat should see: (artifact) + (review instructions) + (full project context). If a skill currently relies on Fresh "reading above," it has this bug.

**Recurrences:**
- 2026-05-01: /architecture (PG optimization plan) — original observation
- 2026-05-02: /deprecate (medlog-stack) — Fresh×2 both refused with identical "you haven't shared the rebuild proposal, Daniel's defense, or any code" message; Deep×2 produced rich convergent output but Deep×Deep convergence is not Ploidy convergence. Confirms the deprecate skill template has the same bug.
- 2026-05-02 (rec 31, second medlog turn): /deprecate re-run on medlog-stack — same pattern: Deep×2 fabricated detailed scenarios with confidence-rated tables; Fresh×2 refused for missing artifact. The Fresh-challenges-Deep seat (which had visibility into Deep's writeup) usefully critiqued Deep's reasoning, but that is not a substitute for an artifact-grounded Fresh seat. Skill remains broken.
