---
name: arch-split 5th-reviewer cross-check (v2)
description: 2026-05-07 second 5th-reviewer Fresh pass over Fresh×2+Deep×2 on the Phase-1 microservices split; AGREE/CHALLENGE/SYNTHESIZE per point + 8 panel-wide gaps
type: project
originSessionId: dffe25e1-a545-4b44-8907-f92de1797897
---
# 5th-Reviewer Fresh Cross-Check (v2) — Phase-1 Microservices Split

Context: B2B FinTech, 280K-LOC Django monolith, 12 backend eng, 0 platform, 99.95%/18mo, 2.4M req/day. CTO directive to extract auth/billing/notifications. Panel = Fresh×2 + Deep×2.

## Fresh Session 1 (18 points)

| # | Point | Verdict | Note |
|---|---|---|---|
| 1 | Decision was mandated, not engineered | AGREE | Load-bearing; panel-unanimous |
| 2 | Velocity diagnosis unsupported | AGREE | RCA absent |
| 3 | Precedent reasoning weak | AGREE | |
| 4 | 0 platform / 0 K8s / 12 eng | AGREE | Capacity arithmetic correct |
| 5 | Operational maturity will regress | AGREE | |
| 6 | No SRE/observability story | AGREE | |
| 7 | Auth first = highest blast radius | AGREE | |
| 8 | Billing without distributed-tx plan | AGREE | Highest-class FinTech risk |
| 9 | Dedicated DB implies unscoped data migration | AGREE | |
| 10 | REST creates chatty bidirectional dep | AGREE | "distributed monolith" |
| 11 | Separate repo loses cross-cutting refactor | SYNTHESIZE | Also breaks atomic DB migrations spanning services; the deeper failure mode beyond "lost type-checking" |
| 12 | 9mo vs 6mo timeline gap | AGREE | Specific catch |
| 13 | No rollback plan | AGREE | |
| 14 | No success criteria | AGREE | |
| 15 | Compliance/audit multiplies | AGREE | |
| 16 | Cheaper interventions not compared | AGREE | Test isolation, feature flags, canary |
| 17 | 28 req/s isn't forcing function | AGREE | |
| 18 | Capability vs product-line seam mismatch | AGREE | Biggest panel-wide miss; load-bearing |

## Fresh Session 2 (~17 points incl. gaps)

| # | Point | Verdict | Note |
|---|---|---|---|
| 1 | Zero platform capacity | AGREE | Dup of F1.4 |
| 2 | Distributed consistency for auth+billing | AGREE | |
| 3 | Auth highest blast radius | AGREE | |
| 4 | Uptime regress (0.9995³≈99.85%) | AGREE | Explicit math sharpens claim |
| 5 | Diagnosis→prescription gap | AGREE | |
| 6 | Quarter/service is optimistic | AGREE | |
| 7 | REST creates distributed monolith | AGREE | |
| 8 | Shared-data migration unaddressed | AGREE | |
| 9 | Coordinated deploy story missing | AGREE | |
| 10 | No tracing/correlation IDs | AGREE | |
| 11 | Contract tests / E2E missing | AGREE | |
| 12 | Decision without technical evaluation | AGREE | |
| 13 | "Last 3 companies" weak | AGREE | |
| 14 | Conway: ~2.4 eng/service | AGREE | Sharper than F1 form |
| Gaps | Success/reversibility/cost/compliance/security/alternatives | AGREE | All correct |

## Deep Session 1 (40 lettered points)

A1 unverified diagnosis — AGREE
A2 90min = migrations+smoke (split won't fix) — AGREE
A3 Wrong seam: capabilities vs product lines — AGREE (load-bearing)
B1 0 platform on 6mo for 5 services — AGREE
B2 On-call model breaks — AGREE
B3 Hiring assumption absent — AGREE
C1 Walking from known-good 99.95% — AGREE
C2 No per-service SLOs — AGREE
C3 No dep graph / failure-mode analysis — AGREE
D1 Distributed tx for billing (saga, outbox, idempotency) — AGREE; FinTech regulatory event
D2 FK cross-boundary inventory needed — AGREE
D3 Audit log correlation for SOX/PCI/SOC2 — AGREE
D4 Schema-evolution coupling persists — SYNTHESIZE (partly: solvable with versioned APIs + ACL, but team won't have time/skill in-window — so practically true)
D5 Data ownership for `users` — AGREE; sharpest D-block question
E1 Notifications first — AGREE
E2 Auth structurally hard for FinTech (latency budget) — AGREE
E3 Billing worst first pick — AGREE
E4 No anti-corruption layer — AGREE
F1 Shared-library hell — AGREE
F2 CI × 4 ownership — AGREE
F3 Contract testing absent — AGREE
F4 Versioning policy — AGREE
G1 No distributed tracing — AGREE
G2 Log correlation — AGREE
G3 Local dev velocity drop 20–40% — AGREE
H1 mTLS / PCI scope expansion — AGREE
H2 Secrets sprawl — AGREE
H3 Authz fragmentation = priv-esc bug class — AGREE
I1 1.5–2.5× cloud spend — AGREE
I2 1.8 engineer-years opportunity cost — AGREE; quantified well
J1 Directive forecloses dissent — AGREE
J2 5/6mo is calendar not engineering — AGREE
J3 CTO precedent non-transferable — AGREE
J4 No success/exit/kill criteria — AGREE

## Deep Session 2 (26 numbered points)

1 Decision before evaluation — AGREE (load-bearing)
2 Capability split ≠ pain (product-line coupling) — AGREE; load-bearing wrong-seam
3 Zero platform capability — AGREE
4 Auth-first inverts blast-radius ordering — AGREE
5 0.9995⁴ ≈ 99.8% (~17.5 hr/yr) — AGREE; sharper than Fresh-2's 99.85%
6 Cross-service FK unscoped — AGREE
7 Distributed tx for billing — AGREE
8 Mid-migration *worse* than today (deploy window grows before shrinking) — AGREE; specific and underweighted by others
9 CTO 6mo vs lead 9mo unresolved — AGREE; surface-it-now framing valuable
10 No contract/SLO between services — AGREE
11 Test isolation is real fix — AGREE
12 On-call math: 12 eng / 4 units = 3/unit, need ≥5 — AGREE; specific
13 Observability gap — AGREE
14 Local dev regression — AGREE
15 4× HA Postgres ops cost (no DBA) — AGREE
16 Schema evolution coordination — AGREE
17 Secrets/config sprawl — AGREE
18 Attrition risk from directive itself — AGREE; underweighted elsewhere
19 Inverse Conway: org topology before code topology — AGREE
20 CTO heuristic context-mismatch — AGREE
21 Async vs REST not justified — AGREE; subtle but right (notifications + billing have natural event shape)
22 Cutover plan absent — AGREE
23 Compliance audit boundary expansion — AGREE
24 JWT/session/mTLS unspecified — AGREE
25 CI cost low — AGREE
26 Versioning strategy unscoped — AGREE

## Net challenges/synthesizes

- **0 hard CHALLENGEs.** Panel is converged.
- **2 SYNTHESIZEs**: F1.11 (separate repo also breaks atomic schema migrations, not just type-checking); D1.D4 (schema-evolution coupling — formally solvable, practically intractable in this team's window).

## Gaps the panel missed (Fresh 5th-reviewer adds)

**G1. API gateway / ingress / TLS termination unscoped (HIGH)**
With 3 services + monolith all reachable, who routes? TLS terminates where? Header propagation? Rate-limit enforcement? Today the monolith is the edge; post-split there must be an explicit edge component. Unmentioned by all four reviewers.

**G2. Background-job (Celery/RQ) ownership during split (HIGH)**
A Django monolith of this size almost certainly has scheduled jobs and async workers (billing reconciliation, notification fan-out, retries, exports). Each job has implicit DB and code coupling. Splitting requires deciding which queue/broker each service uses, who owns the worker, and how cross-service jobs (e.g. "post-charge → send receipt") become events. Panel hits sagas conceptually but never names the worker/broker tier explicitly.

**G3. Postgres connection-pool exhaustion during dual-write (HIGH)**
Dual-write/CDC phases double connections to multiple DBs. Postgres `max_connections` and pgBouncer settings become a hard constraint, especially under spike load. Unmentioned. (This is the kind of operational gotcha that causes a "successful" cutover to fail under prod load.)

**G4. GDPR/DSAR + right-to-be-forgotten coordination (MEDIUM, HIGH if EU customers)**
Once user data lives in 4 stores, a single deletion request becomes a coordinated multi-service workflow with idempotency and audit. Today: one transaction. FinTech B2B + EU exposure makes this a real legal risk; un-scoped.

**G5. Customer-facing SLAs / contractual review (MEDIUM)**
B2B FinTech almost always has uptime/latency SLAs in customer contracts. Splitting billing onto separate availability math (#5/#5) may breach contractual terms; legal needs to bless the SLO regression. Panel discussed SLO internally but not contractually.

**G6. Caching layer ownership & invalidation (MEDIUM)**
If monolith caches `users` data and auth-service becomes source of truth, staleness windows + invalidation pathways must be designed. Panel implicit in D5 (data ownership) but never names cache invalidation as the operational consequence.

**G7. DR/backup posture across N databases (MEDIUM)**
PITR, backup verification, restore drills × 4 DBs. RTO/RPO must be redefined per service. Cross-service-consistent restore is materially harder than monolith. Unaddressed.

**G8. Insurance, vendor support, audit-firm scope (LOW–MEDIUM)**
Each new infrastructure component (mesh, broker, tracing backend, secrets manager) is a new vendor surface and possible audit-scope change. E&O insurance and SOC2 auditor may need to re-scope. Cost is real, panel didn't price it.

## Bottom line

- **Convergence**: 0 CHALLENGE, 2 SYNTHESIZE, ~95+ AGREE across the panel. The panel is converged on **DO NOT PROCEED as scoped**.
- **Load-bearing items** (any one alone justifies halt): wrong-seam (capability vs product line), 0 platform capacity, billing-distributed-tx absence, auth-first blast radius, coercive decision environment.
- **Counter-proposal**: modular monolith + per-product-line deploy gating + extract `notifications-service` only as a learning vehicle. Panel-unanimous.
- **8 fresh gaps** added above, all operational/legal not architectural — these tend to be where confident architectural plans actually fail in execution.

Confidence: **HIGH** that proposal should not proceed; **HIGH** that the 8 added gaps are real and unmentioned.
