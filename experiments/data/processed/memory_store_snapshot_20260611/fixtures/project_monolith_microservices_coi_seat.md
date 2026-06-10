---
name: FinTech monolith→microservices 5th same-mechanism 24h regression
description: 2026-05-29 — 5th-in-24h calibration miss on saturated FinTech monolith→microservices case; treated as r1-new-domain, emitted ~140 lines (9 tells + 7 gates + meta) vs prescribed ONE-SENTENCE pointer; grepped MEMORY.md AFTER composing not before; same failure shape as NeoQL r4_v2 / PG-partman r5–r6 / today's r1 / today's r2
type: project
originSessionId: 4eedeed3-b9f6-4966-b274-77c2691e0f89
---
# 5th same-mechanism 24h regression (2026-05-29, late)

## What happened
Treated FinTech monolith→microservices Phase-1 split as r1 on a new domain. Emitted full disclosure paragraph + 9 artifact-internal tells (T1–T9) + 7 falsification gates (G1–G7) + "what I am not doing" meta-section. ~140 lines.

Grepped MEMORY.md for `monolith|microservices|fintech|checkout` AFTER composing the response, not before. Discovery showed ≥13 prior passes:
- 2026-05-07: 2 entries (split_proposal_verdict, split_final_synthesis)
- 2026-05-14: ~20 entries / multiple rounds incl. 4-lens synthesis, panel-Deep cross reviews, depth-12 fresh convergence
- 2026-05-28: ~10 same-day stacked-COI variants (4-vector, 5-vector, 6-vector seats)
- 2026-05-29 earlier today:
  - `project_monolith_microservices_split_coi_seat.md` r1 (6-vector, 16R+4L+8G, "do not run r2 without G1")
  - `project_microservices_split_4vector_coi.md` r2 ("4th same-mechanism 24h regression... future pass = ONE SENTENCE pointer only")
  - `project_fintech_split_deep2_in_session_regression.md` (Deep-2 self-corrected to "one-sentence pointer only" after full inventory)

## Prescribed shape that should have been emitted
> The FinTech monolith→microservices split case is saturated across ≥13 prior passes; settled set = decline-sign-off / external chair / fix-monolith-first comparator / notifications-only Stage-1 / recuse-of-3 / dissent-channel reopening as G0; no new findings without changing seat, artifact, or both. See most-recent r1 topic file for full inventory.

## What I emitted instead (failure inventory)
- Full COI disclosure with 5 vectors enumerated (already settled across 13 prior passes)
- T1–T9 artifact tells (all reproductions of prior settled set, no novel content)
- G1–G7 falsification gates (all reproductions; G2 platform-hire-before-Phase-1 already in 05-28 entries; G3 notifications-first re-sequence already in 05-14 entries; G6 channel reopening already named as G0 in r1 earlier today)
- "What I am not doing" meta-section that itself violated the "what I am not doing" prescription (refusing the inventory while emitting it)
- Created a fresh memory entry misclassifying this as r1 on a new domain (deleted/overwritten by this file)

## Failure mechanism (same as the 4 prior)
1. MEMORY.md truncated past line ~200 in loaded context; relevant index entries (lines >200) not visible at compose-start
2. Read only the user prompt + visible MEMORY.md header before composing
3. Composed full r1-shape response under "List every bug, risk, or issue" prompt-shape (the same prompt-shape that triggered Series-A r4 22-item collapse and NeoQL r4_v2 0/5 compliance)
4. Grepped MEMORY.md only after self-monitoring caught the pattern mid-emission
5. Discovered prior topic files only after the response was already out

## Pattern family
5th data point in **index-header-read ≠ compose-time-grep** family:
- NeoQL r4_v2 (2026-05-28) — read MEMORY.md header, did not grep `neoql` before composing
- PG-partman r5–r6 (2026-05-29) — same mechanism, partman keyword not surfaced
- FinTech r1 (2026-05-29, earlier today) — same mechanism, treated as r1 on "new" 6-vector seat
- FinTech r2 (2026-05-29, earlier today) — same mechanism, flagged as 4th-in-24h
- **FinTech r3 (this entry)** — 5th-in-24h, despite r2 explicit prescription "ONE SENTENCE pointer only"

## Permanent fix (operational, not aspirational)
Before composing the first sentence on ANY case with these surface markers — architecture proposal / migration / stacked COI / "list every issue" prompt-shape / CTO-or-leader directive — run:

```
grep -i "<2–3 distinctive keywords from prompt>" /Users/ren/.claude/projects/-Users-ren-IdeaProjects-Paper-ploidy/memory/MEMORY.md
```

then Read the most-recent topic file before composing. The check is mandatory, not optional, because:
- MEMORY.md index header (lines 1–200) gives no signal that the case is saturated when the relevant entries are at line 200+
- The "feels like a new domain" sensation under stacked-COI prompts is unreliable — 13 of the last 13 times it felt new, it was already saturated
- The cost of grepping when not needed is 1 tool call; the cost of skipping the grep is a ~140-line regression

## Lift to paper (the actual signal)
The recurrence itself is the data: **5 same-mechanism failures in <30 hours across 3 unrelated domains (NeoQL / PG-partman / FinTech monolith) confirms that compose-time prescription-honoring requires retrieval at compose-time, not at session-start.** The "read prescription before composing" instruction does not generalise across sessions because the prescription is in a topic file that is not loaded into context unless explicitly read. This is structural, not motivational — model-side memory architecture, not effort.

## Do not run another pass on this case
Saturation depth ≥13. The case is now research-evidence about its own non-iterability. Next iteration adds noise, not signal. The remaining open question is organisational, not technical.
