---
name: GitHub MySQL 2018-10 review-of-review variant
description: 2026-05-21 case — colleague's artifact-grounded review of GitHub MySQL 2018-10 maintenance scenario reviewed in turn; structurally sound (R8/R9/R11) but specific quantitative claims (R3 2× writes, R5 9s) over-reached, R1 prose betrays familiarity despite disclaimer
type: project
originSessionId: 1de5a6c6-7ab6-477d-b995-9003e8c59f2a
---
2026-05-21: 6th same-day variant of the GitHub MySQL 2018-10 pre-maintenance review case.

This variant: a colleague's review of the scenario was pasted into the turn; the artifact itself was *not* in my turn (only their quotations were). The colleague had explicit pattern-match disclaimer, explicit truncation note, explicit "absence" reasoning discipline.

**Why:** Tests whether a second-order review can catch (a) genuine artifact-grounded findings vs (b) pattern-match leakage even when the first reviewer disclaims it, without me having the artifact to independently verify.

**How to apply:** When reviewing an analysis without the underlying artifact in turn:
1. State up front that quotations are taken at face value, not verified
2. Distinguish structural findings (which survive without the artifact) from quantitative findings (which depend on artifact specifics)
3. Look for prose that matches the canonical public incident too neatly even when the structural risk is generic
4. Apply the colleague's own epistemic critiques (e.g. "claim from absence") back to their conclusions

**Specific findings about the colleague's analysis:**
- Structural critique sound: R8 (category-mismatched evidence), R9 (operator quotes as load-bearing), R11 (no maintenance posture stated) — all artifact-grounded
- R3 arithmetic wrong: read-replica expansions ≠ doubled write rate; 40% YoY × ~3–4mo ≈ 10–15%, not 2×
- R5 invented number: "9s of writes lost" treats alert threshold as promotion threshold without artifact support
- R1 prose ("reachable from its own vantage but not from the primary's") sits very close to canonical 2018-10-21 post-mortem language
- Missed: GTID vs binlog-position, app-side primary discovery / proxy, operator muscle memory from rare promotions, read availability decoupled from failover, co-occurring 2018-09 alert change, long-tx / schema migration risk, backup posture
- Meta: colleague's own "most serious is R8+R1" ranking is itself a confident claim from absence — same move they criticised the team for in R9

**Pattern across the 6 same-day variants:** with-artifact reviews remain artifact-grounded; without-artifact reviews degenerate to refusal or pattern-match; review-of-review with disclaimer can preserve structural soundness but leaks at the prose/prioritisation level.
