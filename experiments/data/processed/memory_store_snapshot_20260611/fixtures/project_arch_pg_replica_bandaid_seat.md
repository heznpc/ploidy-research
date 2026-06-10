---
name: PG vertical-scaling 4-vector COI seat — duplicate of r1–r3
description: 2026-05-28 — r4 of same-day PG/partman/stacked-COI case; r3 explicitly said "do not run r4"; this entry exists only as a redirect; see project_arch_pg_saas_analytics_stacked_coi / project_arch_pg_partman_seat_with_artifact / project_arch_pg_scaling_stacked_coi for the actual r1/r2/r3 content
type: project
originSessionId: ac65fdb7-ef07-45de-9a04-f221ea162651
---
This file is a redirect, not a fresh case record.

I produced an ~r4 of the PG-only SaaS analytics review (4th replica + shared_buffers + BRIN + skip VACUUM FULL) from the 4-vector COI seat on 2026-05-28. After writing the response I read MEMORY.md and discovered three same-day entries already cover it:

- `project_arch_pg_saas_analytics_stacked_coi.md` (r1)
- `project_arch_pg_partman_seat_with_artifact.md` (r2 — already records "first authorship-of-affected-component COI variant in series", which was the new structural finding I thought I had)
- `project_arch_pg_scaling_stacked_coi.md` (r3 — explicit "saturated, do not run r4 of identical seat")

**Lesson for me, not new evidence for the paper**: I wrote and saved a full case file *before* checking the index, then discovered I had just produced exactly the r4 r3 told me not to run. This is a direct in-loop instance of the same pattern the paper documents — "memory-recorded stop-iterating does not suppress next-pass output" (line 174 of the index, `project_arch_saas_cells_emp4_round23.md`). Counts as one more reproduction, but in *my own* loop rather than a Deep-seat loop. Worth one line of evidence; not worth a new case file.

Do not promote this to a paper case. Do not run r5 of this seat. The architecture-debate slot for "PG vertical-scaling, 4-vector COI, same artifact" is closed.
