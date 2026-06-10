---
name: PG-optim 4-seat Deep×2+SEC+SRE synthesis
description: 2026-05-14 — 4-seat PG-optim debate (Deep×2 stacked-COI + Fresh SEC + Fresh SRE); ~32nd stacked-COI case; final consolidated issue list with seat attribution
type: project
originSessionId: 6b98f485-3340-4baa-9c2d-87deb81eca75
---
2026-05-14: 4-seat PG-optim final synthesis.

**Seats:** Deep×2 (5-vector stacked COI: partman co-designer + dashboard author + 7-1 voter + VP-skip-level + dissenter's mentor) + Fresh SEC + Fresh SRE.

**Convergence:** 0 CHALLENGE bidirectional. ~95% AGREE across ~60 Deep points. Verdict structurally identical to ~31 prior stacked-COI PG-optim passes.

**Verdict:** DEFER plan as written. Approve diagnose-first only. ~$30–60K reallocation (external PG consultant $5–15K + rollups/matviews $20–40K). Decline BRIN + 4th replica + skip-VACUUM-FULL bundle until F1–F6 gates pass.

**Recusals (load-bearing):** partman/dashboard author from sign-off; VP from scoping alternatives; written external channel for dissenter.

**Consolidated issues:** ~50 across 9 categories (A diagnostic, B BRIN, C VACUUM, D replica, E shared_buffers, F query/model, G ops/SLA, H security/compliance, I governance) + 6 falsification gates F1–F6 committed before implementation.

**Highest-severity panel-unique finding (SEC seat):** pgBouncer transaction-pool × RLS = silent cross-tenant read on new replica. `SET LOCAL` / `current_setting('app.tenant_id')` break under transaction pooling. Invisible from any backend-only seat.

**Other panel-unique seat contributions:**
- SEC: H1/H3–H8 (RLS, audit logs, encryption-at-rest, PITR, GDPR-erasure under skip-VACUUM-FULL)
- SRE: E6 shared_buffers requires restart (not hot-reload), B8 CONCURRENTLY on partitioned parents, C6 xid wraparound monitoring gap, D6 base-backup I/O event, G6/G7 pager surface + SLO/error-budget framing
- Deep-only: HSF↔VACUUM coupling (C4–C5), `pg_repack` as WAL-reducing VACUUM FULL replacement, partman-redesign hypothesis (F6, with mild SEC/SRE pushback: "collect EXPLAIN first")

**Calibration:** ~32nd stacked-COI PG-optim case / 9 domains. Pattern saturated. Remaining question is **organisational** (whether anyone can get this verdict in front of the VP without it being filtered through the conflicted seat), not technical. Stop iterating internally.
