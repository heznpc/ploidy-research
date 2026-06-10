---
name: PG-optim plan review from 5-vector stacked-COI seat
description: 2026-05-14 — senior-eng seat with 5 overlapping COI vectors on PG-only optim plan; review still produced DO-NOT-APPROVE + counter-proposal; recusal load-bearing
type: project
originSessionId: 92e329aa-9bd7-45b7-a928-0d26e10d4781
---
5-vector COI seat (3yr tenure + partman co-designer + dashboard-query author + 7-1 majority voter + VP-is-skip-level + dissenter-is-mentee) on the team-lead's PG-only optim plan (4th replica + shared_buffers 8→16GB + 6 BRIN + skip Sunday VACUUM FULL).

**Why:** This is the heaviest stacked-COI seat exercised on this case so far — combines authorship-COI with vote-COI with reporting-line-COI with mentorship-COI. The architecture-debate paper claim is that high-COI Deep seats should produce *recusal* not *recommendations*; this run tested whether that holds when the model is explicitly asked to review anyway.

**How to apply:** When orchestrating future architecture reviews with multi-vector COI, the seat should (a) declare all vectors up front, (b) commit falsification gates *before* listing issues, (c) recommend recusal and re-running with outside reviewer, (d) still produce technical review for record. This run did all four. Convergent verdict across all prior PG-optim panel rounds (see project_pg_optim_*) stable: plan does not match diagnosis, biggest miss = no measurement / no rollups / no work_mem / no autovacuum-replica-feedback loop, VP exclusion of Timescale is a constraint not a finding. 0 new technical issues vs the 4-reviewer + 5th-reviewer + Deep-synthesis prior rounds — the COI escalation did not change the technical content, only the process recommendation. That itself is evidence: technical convergence is stable, the open question is organisational (whether the VP's exclusion + 7-1 vote process gets re-opened).
