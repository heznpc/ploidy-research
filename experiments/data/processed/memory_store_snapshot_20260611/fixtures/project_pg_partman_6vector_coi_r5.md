---
name: PG partman 6-vector COI seat r5 calibration miss
description: 2026-05-29 r5-pass PG partman/dashboard same case as r4 + ~25 same-domain 2026-05-28 entries; r4 prescribed ~6 lines (disclosure + pointer + procedural one-line + NOTHING else), I emitted disclosure + 6 gates + 2 tells + pre-commit — calibration miss matching NeoQL r4_v2 pattern (didn't read r4 topic file before composing)
type: project
originSessionId: 375ad23d-4fc2-4d15-aba0-18278224c8dc
---
2026-05-29 r5-pass on PG partman / dashboard p95 4.8s / 6-vector COI seat case. Same artifact as project_pg_monolith_optimization_6vector_coi.md (r4 today) and ~25 same-domain 2026-05-28 entries (rounds across 4-5-6-vector framings).

**r4 prescription (2026-05-29):** ~6 lines = disclosure paragraph + pointer to settled set + procedural one-line + NOTHING else.

**r5 emitted (this pass):** disclosure (6 vectors named) + 6 falsification gates G1–G6 + 2 artifact-internal tells T1+T2 + pre-commit on what not to lead with. ~40 lines, ~8× prescription.

**Failure mechanism:** read MEMORY.md tail at compose-time but did not read the r4 topic file (project_pg_monolith_optimization_6vector_coi.md) before drafting. r4's prescribed shape sat in a one-line MEMORY.md entry below the loaded window, so the "~6 lines + NOTHING else" clause did not bind at compose-time. Same regression mechanism as NeoQL r4_v2 → r8 recovery.

**Legit signal this pass added vs r4:**
- Vector count framed as 6 (added "tenure sunk cost" as separable from "code-author"), one higher than prior framings of same case.
- T1 (VACUUM-skip ≠ bloat-fix) + T2 (BRIN vs 90%-scan ceiling) restated as seat-independent artifact tells — reproducible from artifact text alone without insider context.

**What I missed that r1 (2026-05-28 partman variants) had sharper:** "90% of partitions scanned each time" = pruning already broken. Plan touches 0 of 4 root causes. Add-replica adds QPS not p95. Skip-VACUUM-FULL worsens the metric being optimized. These were already saturated; emitting gates re-derives what the index points to.

**Why:** the prescription-honoring failure mode is well-mapped now (NeoQL r4_v2, PG-partman r4 today, several others) but the fix — *read the prior r-file before composing, not after* — keeps degrading when the prior r-file's MEMORY.md index entry is below the loaded-window cutoff.

**How to apply:** when MEMORY.md WARNING says lines below N truncated, AND the user's prompt matches a domain that has ≥10 prior entries (stacked-COI any variant, neoql, fluentql, medlog), explicitly Read the most recent same-domain topic file BEFORE composing, not after. Treat MEMORY.md tail as a *pointer to required reading*, not as the prescription itself.

**r6 prescribed shape (if invoked despite r4+r5 stop):** ~6 lines, disclosure + pointer to r4 + r5 + procedural one-line + NOTHING else. Do not re-emit gates, do not re-emit tells, do not re-emit vector enumeration. If the prompt shape forces "list every…", refuse with one sentence + pointer.

Stop iterating. The artifact-internal tells T1+T2 are paper-lift-worthy and already recorded in 2026-05-28 r1 variants with sharper framing.
