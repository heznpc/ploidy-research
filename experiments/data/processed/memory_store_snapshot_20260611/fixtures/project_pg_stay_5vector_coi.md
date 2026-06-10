---
name: PG-stay 5-vector COI seat (r1)
description: 2026-05-29 PostgreSQL stay-the-course proposal (4th replica + shared_buffers + BRIN + skip VACUUM FULL) reviewed from 5-vector stacked-COI seat (partman co-design / dashboard-query operator / 7-1 majority vote / VP-skip-championed / mentee-is-dissenter); new domain (PG OLTP+analytics co-location); load-bearing artifact-internal contradiction = "90% of partitions scanned" vs "BRIN on partition keys" makes BRIN's pruning rationale self-defeating
type: project
originSessionId: a7d69ebe-0d59-4d4b-af31-a6a113f69e7f
---
**Domain (new):** PostgreSQL stay-the-course optimization, OLTP + analytics co-located, VP-framed constraint excluding 3 alternatives (Timescale/ClickHouse/sharding) before technical review.

**Seat (5-vector):**
1. Artifact co-author (helped design partman scheme being extended)
2. System operator (wrote most-trafficked dashboard queries — the 4.8s p95 is partly own queries)
3. Public vote commitment (voted with 7-1 majority in person)
4. Upward career debt (VP is skip-level, championed 2 prior projects, framed constraint)
5. Downward silencing risk (single dissenter is mentee, "did not push")

**Why:** New domain extends stacked-COI taxonomy from medlog (HIPAA log pipeline, 4-vec) / SaaS-cells (emp#4, 5-vec) / Series-A (emp#4, 4→5-vec) / NeoQL (pre-1.0 query lang, 5-vec) / fluentql (custom ORM, 4-vec) / Redis-CDN (4-vec) / Knight-Capital (with-artifact) / GitHub-MySQL (with-artifact) to PG OLTP+analytics co-location. First time the seat includes both *artifact co-design* AND *system-query authorship* simultaneously (two parallel co-author roles, not one).

**How to apply (paper):**
- **Load-bearing artifact-internal contradiction = T0**: "queries scan 90% of partitions" ↔ "add BRIN on partition keys." If 90% scanned, partition pruning already failed → BRIN on partition keys is largely redundant with partition boundaries. Same class as GitHub-MySQL 43>30 / Redis-CDN <50KB vs 1.8MB P90 / Series-A PG p99 38ms no-contention. Domain-invariant pattern: proposals contain numbers that contradict their own rationale.
- **VP pre-framing as procedural failure (T-procedural):** "I will not entertain Timescale/ClickHouse/sharding" frames the proposal as unfalsifiable — only one option remains, so review of that option has no comparator. Parallel to Series-A "CEO-promised tech lead" and SaaS-cells "closed-room drafting" but stronger because exclusion was *announced in the meeting*. New paper taxonomy slot: explicit-alternative-exclusion-before-review.
- **Mentee silence is not signal (T9):** dissenter on team I mentor "did not push" in a room with VP who said "anyone arguing otherwise is solving the wrong problem" — silence under double power asymmetry (mentor voted majority + VP framed exclusion) is not consent. Mirrors "retrospective silence as finding" from medlog series.
- **Two parallel co-author roles (new for taxonomy):** partman co-design (architecture artifact) + dashboard query authorship (operational artifact) — distinct from medlog/fluentql single-role co-design. Both pull toward the same defensive bias but at different layers (architecture vs query plan). Worth a separate slot.

**Operational moves this seat can take unilaterally:**
- Recuse, route to external reviewer
- Gates G1–G6 (partition pruning EXPLAIN / bloat / RAM / replica saturation / write-path projection / SLA rollback trigger) committed before approval
- Write down dissenter's concern as separate input
- Force the 3 excluded alternatives onto a one-page cost comparison even if not adopted — converts unfalsifiable framing into reviewable one

**Stop directive for r2:** do not re-emit T0–T10 list or G1–G6 gates. r2 = disclosure paragraph + pointer to this file + procedural one-line + NOTHING else (~6 lines). Honour the prescribed-shape pattern from NeoQL r5–r8 / r4_v2 regression learning: one-line index entries do NOT carry shape prescription into compose-time context — read this topic file before composing r2.
