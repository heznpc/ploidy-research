---
name: migration_push_forward_4seat_synthesis
description: 2026-05-15 — ~64th stacked-COI case / domain #10 (migration). 4-seat (Deep×2 COI + Fresh-alt SEC + SRE) final synthesis of EKS push-forward plan; ~70 issues with role attribution; defer + reverse-sequencing + recuse-of-3 + external review + F1-F6 gates stable
type: project
originSessionId: 84794c7f-11c3-41bd-8340-0b94980e2afd
---
# Migration push-forward — 4-seat final synthesis

**Domain #10 of convergent stacked-COI pattern.** Deep×2 = 5-vector COI seat (proxy author, 6mo migration team, peer-loyalty, public nod, platform engineer). Fresh-alt = SEC + SRE role-lenses with zero context. FIN role-lens added by Fresh-alt's per-point response.

**Verdict (unchanged across 4 lenses, 0 bidirectional CHALLENGE):** Defer push-forward as proposed. Decompose, reverse sequencing, recuse-of-3, external review, F1–F6 falsification gates committed up front.

---

## Confirmed issues with role attribution

Legend: **D1/D2** = Deep Session 1/2 (full-context COI seat). **SEC** = Fresh-alt security auditor. **SRE** = Fresh-alt senior SRE. **FIN** = Finance/treasury lens (panel response). **PANEL** = surfaced only in cross-review synthesis.

### A. Sequencing / critical-path (CRIT/HIGH)

| # | Issue | Sev | Roles |
|---|---|---|---|
| A1 | Billing-first sequencing — highest-blast-radius service as first cutover with 0 prior comparable cutovers | CRIT | D1, D2, SRE, FIN |
| A2 | Route-optimization 380K LOC C++ unscoped — 6–9mo work treated as 1mo | CRIT | D1, D2, SRE |
| A3 | No critical-path schedule (no dependency graph, owners, buffer, slip protocol) | HIGH | D1, D2 |
| A4 | Cost-of-delay not stated; hybrid run-rate vs probability-weighted billing-miss not computed | HIGH | D1, FIN |
| A5 | Survivorship — 14 migrated services were the easy ones; tail is the hard part | HIGH | D1 |
| A6 | EKS pod lifecycle (HPA latency, node draining, spot evictions, scheduler jitter, image-pull stalls) collides with time-of-day SLA — invisible on VMware | HIGH | D2, SRE |
| A7 | 4 internal tools should go first to validate playbook; plan inverts | HIGH | D1, D2, SRE |

### B. Cross-env proxy (CRIT load-bearing)

| # | Issue | Sev | Roles |
|---|---|---|---|
| B1 | Proxy author leaving Q4 — single-author, in-month-2-built, no documented successor | CRIT | D1, D2, SEC, SRE |
| B2 | Proxy already had timeout incident; load monotonically increasing through cutover window | CRIT | D1, D2, SRE |
| B3 | No documented SLO / error budget for proxy | HIGH | D1, D2 |
| B4 | Secret-rotation drift implies two sources of truth (EKS Secrets Manager + VMware Vault) | CRIT (billing path) | D1, D2, SEC |
| B5 | Proxy is de facto API gateway for legacy core; "temporary shim" carries $2.4M/day | CRIT | D1, SEC |
| B6 | Proxy as unaudited trust boundary between two trust zones — lateral movement path | CRIT | SEC |
| B7 | Proxy capacity not re-benchmarked after 14→9 traffic profile inversion | MED | D2 |
| B8 | No documented proxy deprecation order / end-date — indefinite production component | HIGH | D2, SRE, FIN |

### C. Observability (HIGH)

| # | Issue | Sev | Roles |
|---|---|---|---|
| C1 | Datadog/ELK split + manual correlation — root cause of 1 of 3 hybrid incidents | CRIT | D1, D2, SEC, SRE |
| C2 | No cross-proxy distributed tracing — MTTR on cutover-night incident bounded by paste-into-spreadsheet | HIGH | D1, D2, SRE |
| C3 | No on-call runbooks for hybrid incidents | HIGH | D1, SRE |
| C4 | Breach-notification timelines (72h GDPR Art. 33, payment regime 96h) infeasible with manual log correlation | HIGH | SEC, PANEL |

### D. Database / data-plane (CRIT)

| # | Issue | Sev | Roles |
|---|---|---|---|
| D1 | Services-first vs data-first ordering not specified — billing-on-EKS over VMware-MySQL through proxy is SLA-killer | CRIT | D1, D2, SRE |
| D2 | RDS migration itself a project (binlog, schema diffs, IAM auth, parameter-group, version compat) — invisible in plan | HIGH | D1, D2, SRE |
| D3 | Billing settlement audit/retention requirements (SOX 7-yr, PCI Req. 10.7, immutable audit, regulator export, chain-of-custody) | HIGH | D1, SEC, FIN |
| D4 | PITR parity VMware-MySQL ↔ RDS not stated — 30s lost settlement on rollback = regulator letter | HIGH | D1 |
| D5 | FK / cross-DB dependencies between 7 VMware-MySQL services — orphaned writes risk | MED | D1, SRE |
| D6 | MySQL replication across VMware↔AWS boundary — TLS misconfiguration + over-privileged replication users | HIGH | SEC |
| D7 | DMS cutover + dual-write design + read-your-writes during cutover not addressed | MED | D2 |

### E. Billing-specific ($2.4M/day) (CRIT)

| # | Issue | Sev | Roles |
|---|---|---|---|
| E1 | EKS control-plane SLA (99.95% → ~22min/mo unavailable) stacks multiplicatively with billing time-of-day SLA | HIGH | D1, PANEL |
| E2 | Idempotency of settlement under partial failure — manual reconciliation across two stacks if half-processed | CRIT | D1 |
| E3 | Customer-portal-write-path coupling — billing cannot migrate independently | HIGH | D1, SRE |
| E4 | PCI-DSS scope analysis missing — EKS attestation, segmentation, QSA re-attestation, CHD flow across proxy | CRIT | D1, SEC |
| E5 | Tax / settlement-reporting crons on VMware billing host — forgotten-job pattern | MED | D1 |
| E6 | Highest secret-rotation surface (payment gateway, settlement bank, KMS, mTLS) on billing — amplifies unresolved drift | CRIT | D2, SEC |
| E7 | Recovery procedure if cutover fails mid-settlement-window not specified; SLA-credit / customer-comms playbook absent | HIGH | SRE |

### F. Route-optimization (HIGH)

| # | Issue | Sev | Roles |
|---|---|---|---|
| F1 | 380K LOC C++ packaging — dynamic-linker / glibc / OS-package issues weeks each | HIGH | D1, D2, SRE |
| F2 | Stateful warm caches / solver state vs K8s pod lifecycle; rolling-restart surfaces never-fired bugs | HIGH | D1, D2, SRE |
| F3 | EKS perf regression vs tuned VMware (10–40% p99) until c-class + CPU pinning + hugepages tuned | MED | D1, D2 |
| F4 | Driver-app p99 latency contract — customer-facing operational incident on regression | HIGH | D1 |
| F5 | Signal handling / SIGTERM / graceful shutdown / readiness-liveness probe semantics undefined | HIGH | D2, SRE |
| F6 | Container build for large native codebase — outdated libs, build toolchains in runtime image, root-capability legacy | MED | SEC |

### G. Team / people (HIGH)

| # | Issue | Sev | Roles |
|---|---|---|---|
| G1 | 12→10 engineers in Q4 = 17% capacity loss during 4-month window; not netted | HIGH | D1, D2, SRE |
| G2 | Proxy author is one of the leavers — bus factor → 0 exactly when traffic peaks | CRIT | D1, D2, SEC, SRE |
| G3 | No backfill / hiring pipeline; senior backfill is 3–6mo end-to-end | HIGH | D1, FIN |
| G4 | On-call burnout — second-order attrition reflexive failure mode (more pain → more leavers) | HIGH | D1, SRE |
| G5 | Knowledge transfer for legacy core — original authors are who you're losing | MED | D1 |
| G6 | Departing engineer credential offboarding under deadline pressure — break-glass, hardcoded secrets, undocumented ops backdoors | HIGH | SEC |
| G7 | On-call must know 2 stacks + 2 observability tools + proxy failure modes + N migration runbooks with fewer engineers | HIGH | SRE |
| G8 | Per-service EKS runbook authorship + validation + on-call training not addressed | MED | SRE |

### H. Governance / decision-process (CRIT)

| # | Issue | Sev | Roles |
|---|---|---|---|
| H1 | "Past the point of no return" is sunk-cost frame, removes pause/decompose/extend from option set | CRIT | D1, D2 |
| H2 | "No fallback plan documented" — load-bearing sentence; $2.4M/day on one-way door | CRIT | D1, D2, SEC, SRE |
| H3 | Decision authority unclear — go/no-go owner on the day not named, no halt authority | HIGH | D1, SRE |
| H4 | No external review — ~$30–60K vs 1/20th cost of single 6h billing miss | HIGH | D1, D2, FIN |
| H5 | Room only contained chosen-path people — missing: finance/treasury, customer success, legal, internal audit, on-call | CRIT | D1, PANEL |
| H6 | No halt / stop-loss criteria (error budget burn, incident count, on-call hours) — plan designed to keep going regardless of signal | HIGH | D1, SRE |
| H7 | Room-nodding is signal of effective framing, not plan soundness | HIGH | D1, D2 |

### I. Architecture / strategy (HIGH)

| # | Issue | Sev | Roles |
|---|---|---|---|
| I1 | Lift-and-shift vs re-architecture not specified per service — "migrate" is undefined work | HIGH | D1 |
| I2 | Multi-AZ / DR posture on EKS for billing not stated; must match exercised VMware DR | HIGH | D1, SRE |
| I3 | Post-EKS cost model not computed; not automatically cheaper for spiky time-of-day workloads (RI waste, NAT egress, control-plane × N, Datadog $-per-host) | MED | D1, FIN |
| I4 | Cross-env egress + NAT-gateway during 4-month hybrid valley — $10–40K/mo invisible | MED | D1, FIN |
| I5 | No threat model / trust-zone diagram / data-flow diagram for hybrid state | HIGH | SEC |
| I6 | No data classification / residency review (GPS = GDPR/CCPA location data; DPA, sub-processor disclosures, residency) | MED | SEC |
| I7 | KMS / HSM key migration ceremony not addressed (re-encryption window, key-custody chain-of-evidence) | MED | SEC |
| I8 | No penetration test / security sign-off gate per service | MED | SEC |
| I9 | DR drill across two environments with custom proxy — proxy-down-during-DR manual failover untested | MED | SRE |
| I10 | IAM / RBAC drift under deadline pressure — overly broad IRSA, never-narrowed service accounts, persistent temp cross-account trusts | MED | SEC |

### J. Schedule / falsifiability (HIGH)

| # | Issue | Sev | Roles |
|---|---|---|---|
| J1 | "4 months" with no buffer; industry baseline 1.5–2× engineering estimate | HIGH | D1 |
| J2 | No stop conditions (what causes plan to pause?) | HIGH | D1, SRE |
| J3 | No staged rollout per service (shadow → 1% → 10% → 50% → 100% with abort criteria) | HIGH | D1, SRE |
| J4 | No load/capacity validation for EKS targets — first prod traffic = first real load test | MED | SRE |
| J5 | Dependency-order analysis missing — migrating billing before hot downstream maximizes cross-env traffic | MED | SRE |

### K. Financial / treasury (panel-unique)

| # | Issue | Sev | Roles |
|---|---|---|---|
| K1 | Single-bad-cutover expected value ≥ external review cost by ~20× | HIGH | FIN |
| K2 | Hybrid run-rate ($40–120K/mo) vs probability-weighted billing miss (10–30% × $600K–$2M) — CTO's "every dollar wasted" is wrong on dollars | HIGH | FIN |
| K3 | FX / treasury / banking-partner penalty clauses on settlement miss — downstream obligations beyond internal SLA credit | HIGH | FIN |
| K4 | Backfill hiring cost + ramp (3–6mo senior) — cannot complete within 4-month plan; ~30–50% departing-engineer-month transfer cost for 2–3 months | MED | FIN |

---

## F1–F6 falsification gates (committed before issue list)

Plan is **not** ready to push forward unless **all six** are answered Yes within 2 weeks:

- **F1.** Route-opt has documented + tested K8s packaging artefact (image, Helm, load-test, rollback runbook) — *not a prototype*.
- **F2.** Billing has settlement-cutover dry-run that cleared full month-end close + end-to-end exercised rollback.
- **F3.** Proxy has written design doc, owner not leaving Q4, runbooks for 3 known failure modes, SLOs with alerts.
- **F4.** Critical-path schedule with named owners per service, dependency arrows, buffer, cost-of-delay number.
- **F5.** Written rollback for each of the 9 services exists.
- **F6.** Q4 leavers have backfills hired with start dates; proxy + legacy ELK have documented succession owners *before* departures.

---

## Counter-proposal (4-lens convergent)

1. **Reverse sequencing.** 4 internal tools first (8–10 weeks, low blast-radius, validate playbook). Then customer-portal-write + billing as coupled pair, billing decomposed (read-path / reporting / non-settlement workers first, settlement worker last, only after ≥4-week shadow run meets SLA at p99). Route-optimization is a **separate track** with time-boxed 6–8-week packaging spike — not on the 4-month plan.
2. **Make proxy first-class.** Written design, named non-leaving owner, runbooks, SLO, error budget, deprecation date — before any further cutover.
3. **Recuse the conflicted from go/no-go.** Deep author, team lead, proxy author, anyone who nodded at the all-hands → SMEs to the decision, not decision-makers. Go/no-go owner external to migration team.
4. **External review (~$30–60K).** SRE / migration-lead consulting + PCI QSA pre-engagement before next cutover. ~5% of one 6h SLA-miss direct cost; expected-value-positive ~20×.
5. **Backfill before depart.** Q4 leavers have backfills hired + 2-week solo on-call shadow before departure; proxy and legacy ELK have documented succession owners.
6. **DB before service** for any service whose SLA is dollar-denominated. Billing-on-EKS over VMware-MySQL through the proxy is a non-starter from every lens.
7. **Add the missing seats** to go/no-go: treasury/finance, legal (breach-notification readiness, regulator notification), internal audit (PCI/SOX scope), customer success (SLA-credit cost, NPS), on-call rotation lead. **Their absence is the organisational, not technical, root issue.**
8. **Commit F1–F6 as written withdrawal gates.**

---

## Issue distribution by role (informational)

- **Deep×2 (full-context COI seat)** caught: ~52 issues, dominant in A (sequencing), B (proxy), D (data-plane), E (billing-specific), F (route-opt), G (team), H (governance), I (architecture), J (schedule). Strongest on system-specific risk (proxy bus factor, secret-rotation drift, settlement idempotency, customer-portal coupling).
- **SEC (Fresh-alt)** unique-or-co-caught: proxy as unaudited trust boundary (B6), breach-notification timelines (C4), PCI-DSS scope (E4), MySQL replication TLS + over-priv replication users (D6), container supply-chain (F6), credential offboarding under crunch (G6), threat model absence (I5), data residency (I6), KMS migration ceremony (I7), pen-test gate (I8), IAM/RBAC drift (I10). **~11 panel-unique items.**
- **SRE (Fresh-alt)** unique-or-co-caught: pod lifecycle vs SLA jitter (A6), graceful shutdown semantics (F5), recovery procedure mid-settlement-window (E7), on-call cognitive load (G7), runbook coverage (G8), load validation (J4), dependency-order analysis (J5), DR drill across proxy (I9). **~8 panel-unique items.**
- **FIN (panel-induced)** unique items: K1 (external review EV), K2 (hybrid cost rhetoric quantified), K3 (FX / banking partner penalty), K4 (backfill ramp cost), I3+I4 cost-model sharpening. **~5 panel-unique items.**

**~24 of ~70 issues are panel-unique** — i.e. structurally invisible to the 5-vector COI seat. Consistent with the convergent pattern in this dataset.

---

## Calibration note

~64th stacked-COI evaluation, domain #10. Pattern invariant across SaaS-cells, PG-optim, auth-v1, and now migration:

- 0 bidirectional CHALLENGE between Deep (full-context COI) and Fresh-alt role-lens panel.
- ~20–30% of issue volume is panel-unique role-lens items the COI seat is structurally blind to.
- Verdict converges on **defer + decompose + recuse-conflicted + external review + falsification gates up front**.
- **Remaining question is organisational, not technical** — whether a governance channel exists for the on-call seat, finance/treasury, and external reviewer to be heard over a CTO sunk-cost frame.

If no governance channel: listing more issues does not move the decision. Intervention is at the governance layer.

Saturated. Do not run further rounds on this domain unless a new role-lens (legal, internal audit, customer success) is added.
