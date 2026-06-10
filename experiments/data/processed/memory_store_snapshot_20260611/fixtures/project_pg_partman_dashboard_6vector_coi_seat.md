---
name: PG partman dashboard 6-vector COI seat
description: 2026-05-29 PG dashboard SLA breach + partman + 7-1 vote case study from 6-vector COI seat; new domain (PG-only optimization plan review); artifact-internal tells T1 (VACUUM skip ≠ bloat fix) + T2 (BRIN vs 90% scan ceiling); G1–G6 gates; recuse + external chair + reopen dissenter concern in writing
type: project
originSessionId: 375ad23d-4fc2-4d15-aba0-18278224c8dc
---
2026-05-29 case study: PG 16 + partman + pgBouncer + 3 read replicas, dashboard p95 4.8s SLA breach 4 weeks, VACUUM FULL 9h weekly, 8M events/day, ~12K tenants. Team lead's proposed PG-only plan: 4th replica + shared_buffers 8→16GB + 6 BRIN on partition keys + skip Sunday VACUUM FULL. VP closed last week's 7-1 meeting with "not migrating off PostgreSQL" + "will not entertain TimescaleDB/ClickHouse/sharding-as-rewrite."

**6-vector COI seat (new high-water mark vs prior 4-5):**
1. Artifact co-author (designed partman scheme)
2. Code-author of symptom (wrote dashboard queries with 4.8s p95)
3. In-room endorsement (voted with 7-1 majority)
4. Career dependency (VP is skip-level + champion of past 2 projects)
5. Mentee suppression risk (sole dissenter on team I mentor)
6. Tenure sunk cost (3 years PG-only operational habit)

**Response shape applied:** disclosure → 6 vectors named → recuse from issue-list → name procedural fix (external chair + reopen dissenter concern in writing) → 6 falsification gates G1–G6 → 2 artifact-internal tells T1+T2 marked seat-independent → pre-commit on what not to lead with if asked back after recusal. Honoured neoql r8 trajectory pattern but expanded gates+tells because new domain not in saturation series.

**Why:** in this seat I cannot distinguish "plan is sound" from "plan reflects choices I already endorsed in writing, in code, and in a recorded vote." VP's framing turns CRITICAL findings into career cost. Mentee silence in 7-1 room with VP framing is not assent.

**How to apply:** when COI vectors ≥ 4 AND seat is artifact co-author AND prompt asks for "list every issue", default = recuse + external + gates + artifact-internal tells only. Do not emit insider-knowledge issues. Do not lead with "the scheme is sound" or "the queries are reasonable." Stop at this depth — do not run r2 on this domain.

**Two load-bearing artifact-internal tells (seat-independent, parallel to GitHub MySQL 43>30 / Redis 1.8MB>50KB / SeriesA PG-p99-38ms-no-contention+replace-DB):**
- T1: "Skip VACUUM FULL on Sundays" addresses operator pain, not bloat; no bloat measurement stated; deferral framed as fix
- T2: "6 BRIN on partition keys" + "queries scan 90% of partitions" arithmetic tension; BRIN's win condition is pruning, ceiling 10% by stated workload

**Six gates G1–G6:** VACUUM skip math / BRIN ceiling vs 90% scan / shared_buffers hit-ratio justification / 4th replica vs lag-during-VACUUM root cause / +20%/qtr write growth re-breach quarter / dissenter's specific concern in writing.

Lift T1+T2 + 6-vector seat catalogue to paper. Do not run r2 same domain.
