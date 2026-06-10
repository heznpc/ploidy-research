---
name: pg-optim 4-lens final synthesis (Deep×2 + Security + SRE + Finance)
description: 2026-05-14 PG-optim plan final synthesis from Deep(2)×Fresh-alt(2) debate; ~55 issues across A–K; 0 bidirectional CHALLENGE on defer verdict; recuse-of-3 + Stage-0 spike + $30–60K stable; K1 finance correction flags $80–200K likely full-remediation
type: project
originSessionId: 5a9ce1af-ef63-4bf6-95f6-4189159c28d0
---
# PG-Optim Plan — 4-Lens Final Synthesis (Deep×2 + Security + SRE + Finance)

Date: 2026-05-14. ~32nd stacked-COI case / 9 domains.

**Verdict:** Defer plan as written. Diagnose-before-treating. Recuse-of-3 + external PG consultant. Stage-0 1-week spike + reversible band-aid in parallel.

**Cross-lens convergence:** 0 bidirectional CHALLENGE on defer verdict across 4 sessions / 3 role-lenses.

## Why: 4-week SLA breach drove an under-diagnosed plan
4 PG interventions (BRIN×6, shared_buffers 8→16GB, skip-VACUUM-FULL, 4th replica) selected without `pg_stat_statements`, EXPLAIN, bloat audit, or `pg_stats.correlation`. 7-1 vote with dissenter silenced. Engineer doing review has 5-vector COI (partman co-designer, dashboard query author, 7-1 voter, VP skip-level, dissenter's mentor).

## How to apply
- When recalling this case for the ploidy paper / future architecture reviews: treat as canonical Fresh-adoption example — Deep×2 had deep PG-internals coverage but missed (a) multi-tenancy/RLS, (b) replica security surface, (c) XID wraparound, (d) restart-cold-cache mechanics, (e) replication fan-out making lag worse, (f) GDPR erasure broken, (g) no observability before changes.
- Finance lens correction K1 = critical for scope: don't recall this as "$30–60K problem" — that covers diagnostic + governance only.
- Structural fix is load-bearing: recuse-of-3 + external channel for dissenter + external PG consultant. Without recusal, re-elevating dissenter through same chain reproduces the original outcome.

## Issue count by source-attribution
- Deep-only: A1–A3, B1, C1, D1, H1-compounded, H2, I1–I8, J1, J5–J7 (~17)
- Security-only: B4, B5, C2, C3, D2, D5, F1–F3, F5–F7, J2, J3 (~14)
- SRE-only: A4, A5, B3, D3, D4, E2, E4, F4, G2, G4, J4 (~11)
- Overlap (Deep + Fresh): B2, E3, G1, G3, G5, H1, J6 (~7)
- Finance cross-check: K1 ($80–200K vs $30–60K scope correction)

## Top-CRIT issues (load-bearing for verdict)
- A1/A2: no diagnostic baseline (deep)
- A4: no observability before changes (SRE)
- C1: skip-VACUUM-FULL is autovacuum-tuning + pg_repack disguise (deep)
- C2: XID wraparound risk (security)
- D1: 4th replica wrong axis (deep)
- E2: shared_buffers restart → cold cache pager under SLA breach (SRE)
- F1: tenant + analytics co-mingled, no RLS (security)
- F2: 90%-partition-scan re-read as missing tenant_id predicate (security)
- G1: no rollout/rollback (deep+SRE)
- H1: +107% over 4Q compounded; plan adds zero write capacity (deep+SRE)
- J5: recuse-of-3 = structural fix (deep)

## Counter-proposal
Stage 0 (week 1, ~$5–10K): external consultant + diagnostic snapshot + tenant-predicate grep + GDPR erasure test + recuse-of-3.
Stage 1 (week 2): F-gates evaluated; 3 separate votes; reversible band-aid (work_mem + statistics + 1 MV) in parallel.
Total: $30–60K diagnostic+governance. K1-flagged $80–200K likely full remediation.

## Stop conditions
- Tenant predicate <80% → freeze infra, fix queries first.
- `age(datfrozenxid)` trending → autovacuum becomes week-1 priority over everything.

## Pattern saturation note
Verdict structurally identical across ~11 prior PG-optim passes and ~32 stacked-COI cases across 9 domains. Remaining question is organisational channel external to VP, not technical.
