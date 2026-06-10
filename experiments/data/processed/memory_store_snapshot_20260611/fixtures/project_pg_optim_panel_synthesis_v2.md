---
name: project_pg_optim_panel_synthesis_v2
description: PG-optim 4-seat (Deep×2 COI + Fresh-alt Security + SRE) cross-review; 6 high-impact role-lens findings beyond COI seat; full-context lens adds 5 more
type: project
originSessionId: 6a1a9fe0-3c37-489c-ba31-eb9c8fcf901f
---
# PG-Optim Panel Synthesis (Deep×2 COI + Fresh-alt Security + Fresh-alt SRE) — 2026-05-14

~28th stacked-COI PG-optim case. Verdict structurally identical (defer + diagnose-first + recuse-of-3 + ~$30–60K + external consultant).

**Why:** Saturated technical surface. The new value of this panel was the role-specific lenses (security + SRE) surfacing what the senior-backend COI seat structurally under-weighted.

**How to apply:** Treat as the canonical worked example of "role lenses catch what COI seats miss." Use these specific findings when reviewing similar PG-optim plans.

## 6 new high-impact findings the COI seat missed

1. **xid wraparound monitoring not addressed** (SRE #15) — CRITICAL. Skipping VACUUM FULL without `age(datfrozenxid)` alerting → forced read-only mode in months. COI seat owned VACUUM policy → missed it.
2. **shared_buffers 8→16GB requires restart per replica** (SRE #1) — HIGH. Cold-cache spike on a system already at 4.8s p95.
3. **`max_standby_streaming_delay` query cancellations** (SRE #8) — HIGH. Replicas serving dashboards get query cancellations during replay catch-up.
4. **pgBouncer transaction-mode breaks RLS via session GUCs** (Security #8) — HIGH. `current_setting('app.tenant_id')` + RLS isolation primitive broken by pool mode. Potential cross-tenant exposure.
5. **GDPR right-to-erasure SLA via skipped VACUUM FULL** (Security #4) — HIGH. Tombstoned tenant data lingers in heap pages → measurable compliance exposure.
6. **No `pgaudit` / audit-log shipping on new read path** (Security #7) — HIGH. SOC2/HIPAA controls require trails on every customer-data read path.

## 5 full-context gaps even the 4-seat panel missed

1. partman retention-policy ↔ skip-VACUUM-FULL accounting (HIGH)
2. The "8M events/day, +20%/qtr" number itself is uncited — F1–F6 should validate workload number
3. Connection-pool exhaustion at peak (12K tenants × concurrency × pool size) — 4.8s p95 may include acquisition wait
4. Replication slot retention risk on adding 4th replica — primary WAL retention → disk fill → outage (HIGH)
5. **The dissenter's actual dissent text was never quoted** — all 4 seats inferred her position from seniority; nobody read the transcript

## Calibration

Pattern saturated. Verdict stable across ~28 passes. Remaining question is organisational channel external to the VP-COI chain. Stop iterating internally.
