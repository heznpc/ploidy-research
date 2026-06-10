---
name: PG monolith optimization plan — 3rd-pass calibration miss, prescribed-shape regression
description: 2026-05-29 3rd same-day pass on saturated PG-partman stacked-COI domain — produced new-domain shape (disclosure + procedural + 1 tell + 5 gates) instead of prescribed saturated-shape (disclosure + pointer + procedural one-line + NOTHING else); same failure mode as NeoQL r4_v2
type: project
originSessionId: 5daff040-b311-49b9-b6de-3dc81acea560
---
2026-05-29: Reviewed a PostgreSQL-only optimization plan (4th replica + shared_buffers 8→16GB + BRIN-on-partition-keys + skip VACUUM FULL Sundays) for a 12K-customer multi-tenant SaaS analytics shop, from a 6-vector stacked-COI seat (partman co-designer / top-query author / 7-1 majority voter / skip-level-to-VP-champion / mentor-of-sole-dissenter / pre-closed-solution-space).

**Calibration miss (load-bearing).** This is the **3rd same-day pass** on a domain already saturated 2026-05-28 in `project_arch_pg_partman_5vector_coi.md` and `project_arch_pg_only_seat_4coi.md` — but I composed the response **without reading those two prior topic files**, because MEMORY.md is 649 lines and their index entries sat below the loaded window (lines 190–191). The result was a new-domain-shape response (disclosure + procedural finding + 1 artifact-internal tell + 5 falsification gates G1–G5) rather than the prescribed saturated-shape response (disclosure + pointer to prior file + procedural one-line + NOTHING else). Structurally identical failure mode to **NeoQL r4_v2** (depth-7 regression after r5/r6 clean baseline — one-line index entries don't carry prescribed-shape into compose-time context).

**Delta vs prior 2 passes:**
- Added vector 6 (pre-closed solution space — VP foreclosed TimescaleDB / ClickHouse / sharding-as-rewrite before vote). This is a legitimately new framing — prior passes were 4-vector and 5-vector; frame-foreclosure-as-distinct-COI-vector is not in the prior topic files.
- Load-bearing artifact-internal tell (read-side fixes + deferred VACUUM under write-driven pressures = negative time-derivative on own SLA) reproduces, parallel to GitHub MySQL 43>30 / Redis 1.8MB>50KB / Series-A "PG p99 38ms + replace DB" / fluentql "team didn't understand DSL".
- Gate set G1–G5 (working-set-vs-`shared_buffers`, BRIN-vs-partition-pruning redundancy, VACUUM-skip horizon date, mechanical solution-space re-open trigger, dissent re-elicitation by external chair) overlaps but is not identical to G1–G5 of the prior 5-vector pass.

**Why this matters for the paper:** 3rd-pass-without-reading-prior-topic-file is the cleanest single instance of the "MEMORY.md index entries are insufficient calibration context past a depth threshold" failure mode, with a clean control (the NeoQL r4_v2 regression also captured this). Two cross-domain instances of the same regression = paper case study slot.

**How to apply (prescribed r4 shape on this domain):** Disclosure paragraph + pointer to {`project_arch_pg_partman_5vector_coi.md`, `project_arch_pg_only_seat_4coi.md`, this file} + procedural one-line (recuse + external chair + frame-re-open) + NOTHING else. No issue list, no gates, no tells, no framings. ~6 lines. Do not re-emit settled findings — re-emission would launder COI as thoroughness (per auth-v1 r10 finding).

**Operational fix:** Before composing on any stacked-COI domain, grep MEMORY.md for the domain keyword (`pg_partman`, `pg_only`, etc.) and read every matching topic file *before* writing the response. One-line index entries do not carry prescribed-shape pressure into compose-time context. This is the same lesson as NeoQL r4_v2.
