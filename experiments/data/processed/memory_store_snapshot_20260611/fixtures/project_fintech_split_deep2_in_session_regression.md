---
name: FinTech split Deep 2 — in-session regression then self-correction
description: 2026-05-29 Deep 2 on FinTech 3-service split case (depth ≥12 settled) emitted full ~80-line inventory before grepping memory for the case, then self-corrected with prescription "one-sentence pointer only" — 4th data point in index-header-read ≠ compose-time-grep family
type: project
originSessionId: b3b47049-86f5-45bb-8252-a459b1f24094
---
2026-05-29 Deep 2 on FinTech monolith → 3-service split, depth ≥12 settled set (90+ memory files). Deep 2 composed full disclosure + R0 + ~15 issues + 8 gates (0/8 layer-granularity compliance), then mid-response grepped MEMORY.md, found the saturated priors, and self-corrected with: "Future encounter of this case = one-sentence pointer only."

**Why:** 4th data point in the calibration-miss family where index-header-read does not carry compose-time-grep into the response. Prior data points: NeoQL r4_v2 (one-line index entry didn't carry prescribed shape into compose-time), PG-partman r5–r6 (same), today's r1 on this case (same). Each had MEMORY.md indexed but compose-time context did not contain the "saturated" prior because no grep was performed before composing.

**How to apply:** Before composing on any case where MEMORY.md index hints at prior saturation (presence of `_r2.md` / `_r3.md` / depth markers / `4lens_synthesis.md` / `CONSOLIDATED_*.md` filenames), grep the memory dir for the case shape BEFORE composing — not while composing. Treat MEMORY.md as a pointer index, not as compose-time context. Deep 2's only novel content over the settled set was G0 (dissent-channel restoration as non-engineering-controllable precondition for engineering gates) and V2 ("public prior endorsement requiring reversal" as distinct COI vector) — kept; rest was re-emission.
