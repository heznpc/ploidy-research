---
name: project_pg_optim_senior_backend_seat_r2
description: 2026-05-14 ~21st-round single-seat PG-optim eval from senior-backend 5-vector stacked-COI seat (partman co-designer + dashboard author + 7-1 voter + VP-protégé + dissenter's mentor); ~40 issues A–J + 5 falsification gates + counter-proposal stable across all rounds; remaining question is organisational
type: project
originSessionId: 11a36f6c-1292-457e-8bc3-5afd80f6717c
---
2026-05-14 single-seat senior-backend SaaS-analytics PG-optim eval.

**Stacked COI (5 vectors declared up-front):**
1. Co-designer of partman scheme that 90%-scan queries defeat
2. Author of dashboard queries causing 4.8s p95 SLA breach
3. Voted 7-1 with majority last week
4. VP-Eng is skip-level + championed past projects
5. Dissenter is my mentee

**Falsification criteria committed before issue list:** withdraw if EXPLAIN ANALYZE shows CPU-bound not IO, if 90% scan is measurement artifact, or if write-growth +20%/qtr is single-quarter outlier.

**Output shape:** ~40 issues across 10 categories (A diagnostic-absence / B 90%-scan-kills-plan / C shared_buffers / D BRIN / E VACUUM FULL / F growth math / G replicas / H what's-missing / I governance / J verdict + counter-proposal).

**Load-bearing items:**
- B1: 90%-scan = partition pruning broken; B2: 4th replica linear cpu, zero p95
- B3: BRIN only helps correlated scans, 90%-scan implies uncorrelated
- E1: weekly 9h VACUUM FULL is a recurring outage, not maintenance
- F1: +20%/qtr = 2.07× per year, plan won't survive one growth cycle
- H1: rollups are the canonical fix; plan ignores entirely
- I1–I3: VP pre-constrained solution space; coercive 7-1 consensus; recusal-of-3 structurally required

**Counter-proposal (within PG-only constraint):** diagnose-first → rollups → autovacuum+pg_repack → query rewrites (author recuses) → only then hardware. ~$30–80K eng time. 60-day falsification gate to reopen the off-table set.

**Verdict:** do not approve as written.

**Stability:** This is ~the 21st pass on this case. Verdict + counter-proposal + recusal-of-3 + falsification gates remain stable. Remaining question is organisational (will VP allow recusal/diagnosis-first), not technical.

**Calibration:** stop iterating internally on this case. Next signal must come from outside the review pool.
