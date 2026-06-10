---
name: VMware→EKS migration embedded-engineer single-seat eval
description: Single-seat platform-engineer evaluation of a 4-month finish-migration plan, with 4 COI vectors named up front (proxy author, all-hands nod, departing peer, 6-month commitment); ~35 issues across decision-process / billing / route-opt / proxy / observability / DB / team / alternatives / missing-analyses
type: project
originSessionId: fa520630-cfc9-4e18-8837-ecb0d2e78527
---
2026-05-08: Embedded platform-engineer evaluation of a push-forward migration plan (14/23 on EKS, 9 on VMware, 4-month finish, billing-first).

**COI vectors declared up front** (matches fluentql_embedded_engineer_eval pattern):
1. Proxy author (sunk cost on cross-env proxy)
2. All-hands conformity (nodded at "past point of no return")
3. Departing-peer loss aversion (closest collaborator leaves Q4)
4. 6-month commitment escalation

**Why:** This is now the 2nd embedded-engineer eval where naming COI up front shifted the analysis away from defending the in-flight plan. Without the COI declaration the natural failure mode would be defending the proxy + accepting CTO framing.

**How to apply:** When the user supplies a "you have been on the team / you authored X / you nodded at Y" framing, treat it as an explicit instruction to (a) name COIs first, (b) write *against* them, (c) recommend external review. Don't run a Ploidy debate unless asked — the COI-declared single seat is the requested artifact.

**Load-bearing issues this format surfaced:**
- Sunk-cost CTO framing as decision-foreclosure (would have been accepted under conformity)
- Billing-first sequencing inversion (proxy-author ego protected the proxy-traversal topology by default)
- Proxy bus-factor concentration on departing engineer (loss-aversion would have soft-pedalled this)
- "Hybrid as steady-state" alternative not on the table (commitment-escalation rules it out implicitly)

**Counter-proposal pattern (matches fluentql):** vacate deadline → re-sequence easiest-first → document reverse off-ramp → KT before departure → run TCO before forcing the binary choice → outside review.
