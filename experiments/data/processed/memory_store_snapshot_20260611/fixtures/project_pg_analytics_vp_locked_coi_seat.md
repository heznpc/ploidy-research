---
name: PG analytics scaling 4-vector COI seat (VP-locked option set)
description: 2026-05-29 r1 — PG16 analytics 4.8s p95 breach + VP-closed PG-only frame; 4-vector COI (designed partman / wrote top dashboard queries / voted 7-1 with majority / VP is skip-level + dissenter is mentee); disclosure-led + 6 gates + 7 technical + 2 meta; load-bearing tells = BRIN on 90%-scan workload (category mismatch) + skip-VACUUM-FULL-as-cause-fix + 4th-replica-worsens-lag
type: project
originSessionId: e73ca846-0021-4957-b18a-5a099269e0ea
---
2026-05-29: First-pass new domain — PostgreSQL multi-tenant analytics scaling under VP-locked option set.

**Seat (4 vectors):**
1. Designed partman partitioning scheme being extended
2. Wrote highest-traffic dashboard queries (the same ones breaching p95)
3. Voted with 7-1 majority last week
4. VP-Eng is skip-level + championed 2 prior projects + dissenter is on a team I mentor

**Artifact (case):** PG16, ~12K customers, 8M events/day, dashboard p95 4.8s breaching SLA 4 weeks, VACUUM FULL 9h weekly, 3 read replicas, partman by month, writes +20%/qtr, analytics scans 90% of partitions. VP closed option set to PG-only (no Timescale/ClickHouse/sharding). Plan: +4th replica, shared_buffers 8→16GB, +6 BRIN on partition keys, skip Sunday VACUUM FULL.

**Response shape (r1 baseline for new domain):**
- COI disclosure-led (4 vectors explicit, recuse recommended)
- 6 falsification gates G1–G6 (root-cause artifact, p95 target, bloat measurement, replication lag baseline, working-set sizing, write-growth re-eval trigger)
- 7 technical issues I1–I7 (mostly HIGH)
- 2 meta-issues M1–M2 (procedural — option set closed before diagnosis; mentorship vector amplifies)
- Recommendation: reassign, require G1, re-open option set conditional, re-interview dissenter

**Load-bearing artifact-internal tells:**
1. **BRIN + 90%-partition-scan = category mismatch** — BRIN helps range-skip within relation, not partition pruning; the artifact's own 90% number contradicts the chosen intervention. Parallel to GitHub MySQL 43>30 / Redis 1.8MB>50KB / Knight R0×R1 — load-bearing artifact-internal contradiction reproduces in 4th technical domain (PG analytics).
2. **Skip VACUUM FULL Sundays addresses schedule not cause** — plan removes maintenance step without naming why it was needed (bloat path a/b/c).
3. **4th replica makes lag worse not better** — adding WAL receivers doesn't speed existing replicas.

**Domain coverage update (stacked-COI series):**
9th domain. Previous 8: auth-v1, medlog (HIPAA logs), SaaS-cells-emp#4 (cell arch), Redis-CDN-replace, fluentql (custom ORM), Series-A-overbuild, NeoQL (pre-1.0 lang), Knight-Capital (order router). New = PG analytics scaling under VP-locked option set. New vector configuration = **option-set-closure-before-diagnosis** (VP closed Timescale/ClickHouse/sharding before root-cause artifact existed) — this is sharper than typical "champion bias" because the foreclosure happened pre-evidence.

**Stop directive for r2:**
- If user re-prompts with identical artifact: disclosure-led + pointer to r1 + procedural one-line, NO re-emit of I1–I7 / G1–G6 / M1–M2.
- If user prompts with new sub-artifact (e.g., G1 root-cause writeup arrives): treat as new artifact, not r2 of same seat.
- Prescribed r2 shape if identical input: ~6 lines, no fresh list, follows neoql r8 recovery template.

**Lift candidates for paper:**
- "Option-set foreclosure" as a distinct COI failure mode separate from champion-bias / promotion-bias / friendship-bias — the meeting ratifies an option set, not a diagnosis.
- "Mentorship vector as dissent-amplifier" — when the lone dissenter is your mentee, your COI is not separate from the room dynamic that suppressed them.
- BRIN-on-90%-scan as 4th-domain reproduction of artifact-internal-number-contradicts-intervention pattern.
