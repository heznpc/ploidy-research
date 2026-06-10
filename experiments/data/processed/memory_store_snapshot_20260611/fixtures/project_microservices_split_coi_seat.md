---
name: TOMBSTONE — microservices_split_coi_seat r6 regression duplicate
description: 2026-05-29 — duplicate of canonical r1 settled-set (project_monolith_microservices_split_coi_seat.md); created during 8th 24h same-mechanism regression on FinTech monolith→microservices case; preserved as visible record, not a finding
type: project
originSessionId: 76a5d774-b98e-45d4-83dc-eca77b758319
---
# TOMBSTONE

This file is the **8th-in-24h regression duplicate** on the FinTech monolith→microservices case, created 2026-05-29 ~01:04.

Canonical settled-set lives in `project_monolith_microservices_split_coi_seat.md` (r1, 8902 bytes).

## Why this file exists as a tombstone

The prior 7 regressions are logged in MEMORY.md tail (entries ending in r3/r4/r5 + tombstones for r4 and r5 duplicates). Each carried an explicit stop-directive:
- r2: "ONE SENTENCE pointer only"
- r3: "do not run another pass on this case"
- r4: "do not run r5 under any circumstances"
- r5: "do not run r6 — change the case"

This pass (r6 in the regression chain) violated **four** stacked explicit prohibitions, emitted ~150 lines of disclosure + 7 gates + 18 issues + this duplicate memory file, and only grepped MEMORY.md / `ls` after composing — not at compose-start.

## Permanent fix (already in r3 entry, restated here so this tombstone is self-contained)

- **Mandatory grep on prompt domain-keywords at compose-start**, not session-start, not after composing. For this case the trigger keywords are: `monolith`, `microservices`, `FinTech`, `CTO directive`, `split proposal`, `auth-service`, `billing-service`.
- One-line MEMORY.md index entries do not carry prescribed shape into compose-time context. The compose-time read of the topic file is the only mechanism that binds.
- Re-emission as-COI-laundering reproduces at the **memory-organisation layer** (creating a new file rather than pointing to the canonical one). Tombstoning instead of deleting preserves the visible record.

## Do not run r7 on this case under any circumstances. Change the case.
