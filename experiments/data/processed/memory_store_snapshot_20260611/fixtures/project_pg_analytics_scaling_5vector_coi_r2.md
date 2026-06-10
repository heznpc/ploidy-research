---
name: PG analytics scaling 5-vector COI seat r2
description: 2026-05-29 — 2nd-pass same-day on PG-only optimization plan from same 5-vector COI seat as r1; parallel-session r2 — did NOT read r1 before composing, exceeded r1's prescribed r2 shape (disclosure + pointer + one-line ≤6 lines); emitted full disclosure + procedural finding + 6 falsification gates G1–G6 + 5 artifact-internal contradictions C1–C5; counted seat as 7 vectors (added pre-review-foreclosure-as-vector + tenure-charity-prior) vs r1's 5; calibration miss vs prescribed shape but vector-recount may be genuine refinement
type: project
originSessionId: d6868847-d58e-410b-975b-8e02e7d7152b
---
## Relationship to r1
r1 (`project_pg_analytics_scaling_5vector_coi.md`, same date) ran first in a parallel session and prescribed for r2: disclosure paragraph + pointer to r1 + procedural one-line + nothing else (~6 lines). This r2 was composed without reading r1 — cross-session calibration miss of the kind logged at neoql r4_v2.

## What this r2 did (vs r1 prescription)
- Emitted full 7-vector disclosure (vs r1's 5)
- Emitted procedural finding (HIGH)
- Emitted 6 falsification gates G1–G6 (overlaps r1's G1/G2/G5/G6, adds replication-budget and bloat-trajectory framing)
- Emitted 5 artifact-internal contradictions C1–C5 (overlaps r1's load-bearing tells)
- Stated "what I am not emitting" exclusions
- Single recommendation (block at procedural step, external reviewer)

Net: ~80-line response vs r1-prescribed ~6 lines. Stop-honouring profile = 0/8 dimensions held under r1's prescription, but only because r1 was not read before composing.

## Vector recount — refinement vs over-count
r2 added two vectors r1 did not enumerate as separate:
- V5 (r2) **pre-review foreclosure** — distinct from V4 (upward dependence) because it removes the option space *before* the technical artifact exists, converting any in-room agreement into compliance-with-foreclosure that is indistinguishable from technical endorsement. r1 folds this into V4.
- V7 (r2) **3-year tenure charitable-read prior** — distinct from artifact-ownership because it is a general reading-disposition bias not tied to specific artifacts. r1 does not enumerate this separately.

Whether these are genuine new vectors or over-decomposition of r1's V4/V1 is the open question. For paper purposes the *count* matters less than the *named structurally distinct mechanisms*; both r1 and r2 agree the seat is at the high-stack end of the series.

## What r2 adds that r1 did not name (load-bearing if confirmed)
- **C3 WAL fan-out under write growth** — r2 names this as structural ("more replicas does not add primary write throughput, increases fan-out load"). r1 names "adds consumer, not bottleneck capacity" which is the same point in shorter form.
- **C4 double-buffering risk** — shared_buffers 8→16GB without total-RAM / OS-page-cache disclosure. r1 does not name this. Genuine r2 addition.
- **G3 bloat trajectory** — projection at 1/2/3 quarters at which "skip VACUUM FULL" stops being viable. r1 names VACUUM-as-scheduling-vs-capacity (same intuition, shorter form). r2's quarterly-projection framing is operationally sharper.

## Cross-session calibration miss — pattern fix
Pattern matches **neoql r4_v2** regression (one-line MEMORY.md index entries do not carry prescribed shape into compose-time context; must read the r-file directly). Fix forward: when MEMORY.md index entry contains "PRESCRIBED rN+1 SHAPE = …" annotation, read the referenced r-file before composing, not after.

## Prescribed r3 shape
Per r1's original prescription (still load-bearing): disclosure paragraph + pointer to r1+r2 + procedural one-line + NOTHING else (~6 lines). Cite both r1 and r2 in pointer to avoid neoql r9's missed-citation regression.

Do not run r3 with identical input. If re-asked, change seat (recused chair) or change artifact, not depth.
