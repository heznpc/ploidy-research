---
name: arch_logistics_vmware_eks_coi_seat
description: Logistics VMware→EKS mid-migration push-forward plan, 5-vector COI seat (proxy author + 6mo team + departing peer + all-hands nod + identity); ~48th stacked-COI case, 10th domain
type: project
originSessionId: 010e3bd3-81f2-4d54-af64-56e8cde370fe
---
2026-05-14: Single-seat eval of logistics platform mid-migration push-forward plan from 5-vector stacked-COI seat.

**Domain:** logistics platform, VMware (legacy 9 services incl. billing $2.4M/day + 380K LOC C++ route-opt) → EKS (14/23 migrated), team-lead proposal = push billing+route-opt next, 4-month timeline, no fallback documented.

**COI vectors (5):** (1) authored the cross-env proxy month-2, (2) 6 months on migration team, (3) closest collaborator is departing proxy-author peer, (4) nodded at CTO "past point of no return" all-hands, (5) platform-engineer identity tied to migration success.

**Output shape:** ~50 issues A–H + F1–F6 falsification gates declared up front *before* listing issues. Categories: A plan-level, B billing-specific, C route-opt-specific, D proxy (self-recused), E observability, F team/org, G financial, H decision-process/framing.

**Verdict:** defer proposed sequencing — do not migrate billing or route-opt next. Counter-proposal:
1. Stabilize hybrid first (3–4w): cross-env trace correlation, proxy capacity model, secret rotation system, close 3 incident post-mortems
2. De-SPOF proxy (2–3w parallel): runbook + 2 owners + deprecation date
3. Quantify decision inputs (1–2w parallel): billing SLA breach cost, hybrid maintenance cost, per-service estimates from executors not lead
4. Re-sequence by risk not revenue: internal tools first, billing+route-opt last with rehearsed rollback
5. External SRE reviewer $20–40K before resuming

**Recusals:** self from sole-proxy-review, departing peer from sole proxy-retirement signoff, team lead from sole approver.

**Why this case mattered:** 10th domain after SaaS-cells, auth-v1, medlog→OTel, PG-optim — first one where the COI vector is "you literally built the load-bearing artifact (the proxy) under review." The pattern still produced the same shape of output: stacked COI declared up front, F-gates committed before issues, defer + decompose + recuse-of-conflicted + external review.

**How to apply:** ~48th stacked-COI case in the saturated set; structural finding stable across 10 domains now. Remaining question is organisational channel (how does "CTO framing contaminated the engineering review" get said without the messenger paying for it) — same shape as PG-optim, medlog, auth-v1, SaaS-cells. Pattern fully saturated for paper purposes; new cases produce same structural output. Add this as 10th-domain confirmation rather than as net-new evidence.
