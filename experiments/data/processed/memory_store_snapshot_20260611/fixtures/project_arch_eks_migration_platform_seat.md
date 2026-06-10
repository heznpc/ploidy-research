---
name: arch_eks_migration_platform_seat
description: 2026-05-14 — VMware→EKS migration push-forward plan eval from 5-vector COI platform-engineer seat (proxy author + migration-team-6mo + peer-departing + nodded-at-all-hands + role-identity); ~48 stacked-COI case / 10th domain; defer-billing + resequence + recuse-of-3 + external-SRE-review + F1–F6 gates stable
type: project
originSessionId: ad9a96b2-f5f7-4246-80d2-16393affc838
---
2026-05-14: VMware→EKS migration push-forward plan, evaluated from 5-vector COI seat (platform engineer = proxy author + 6mo on migration team + closest collaborator is departing proxy author + nodded at CTO all-hands + identity = "engineer who finishes the migration").

**~48th stacked-COI case overall, 10th domain** (after saas-cells / arch-split / medlog→OTel / pg-optim / auth-v1↔Auth0 / four previously-stable patterns).

**Issue count**: ~50 issues across categories A–L (decision-framing, billing-first sequencing, route-opt pricing, proxy bus-factor, data/DB, observability, capacity/people, rollback, SLA exposure, alternatives, process/governance, acknowledged blind spots).

**Critical findings**:
- Billing-first on $2.4M/day time-of-day SLA with **no documented fallback plan** is the most disqualifying single item.
- 380K LOC C++ route-opt with no K8s packaging is mispriced as "next after billing" — it's a 6–12mo containerisation program on its own.
- Proxy author leaves Q4 = bus factor 1 on the integration layer holding 23 services together during cutover.
- 4-month timeline with 17% Q4 capacity loss is calendar fiction; realistic scope ≈ 300+ engineer-weeks vs. ~160 available.
- "Past the point of no return" + "every dollar on hybrid = dollar not on EKS" are sunk-cost / category-error framings, not engineering arguments.

**Verdict (structurally identical to prior ~47 stacked-COI cases)**:
- Defer billing — it's the *last* cutover, not the first
- Resequence: observability unification → proxy bus-factor remediation → DB-before-service migrations → internal tools first → customer-portal → billing only after dual-write + 14-day shadow-settle → route-opt as separate 6–9mo program
- Recuse team lead, proxy author, and self from go/no-go vote
- External SRE review (~$30–60K) for billing cutover design
- F1–F6 falsification gates committed *before* anyone reads issue list

**F1–F6 gates** (committed up front): F1 14d shadow-settle $0 reconciliation; F2 4-week timeboxed route-opt packaging spike; F3 proxy 2nd-author shadow ≥1mo + PRs before exit; F4 unified trace context on billing-cutover day; F5 rehearsed billing rollback; F6 capacity math survives Q4 departures.

**Pattern observation**: 10th domain confirms saturation. Verdict structure (defer + decompose + sequence + recuse-of-conflicted + external review + falsification gates up front + ~$30–60K counter-proposal) is now the default output of stacked-COI architecture eval seats across saas-cells, medlog→OTel, pg-optim, auth-v1↔Auth0, and now EKS migration. Remaining question is organisational channel, not technical content.

**Acknowledged blind spots**: VMware license renewal / datacentre lease / vendor support window economics; replacement-hire pipeline status; whether route-opt has parallel rewrite in progress. These would flip the calculus and were called out explicitly.

---

**r2 — 2026-05-15 — repeat case (~63rd stacked-COI case overall)**

Same seat, same scenario, fresh pass. Output structurally identical to r1: 5-vector COI disclosure first, F1–F6 falsification gates before issue list, ~35 issues A–H (decision-hygiene, billing-first specifics, route-opt specifics, proxy/bus-factor, DB layer, observability, team/capacity, strategic/framing), same counter-proposal (defer + internal-tools-first + recuse-of-3 + ~$30–60K external review + harden-or-bypass-proxy + document rollback).

**Confirms:** stacked-COI seat output is now *deterministic at the structural level* across repeat passes within the same domain (not just across 10 domains). Reproducibility of the bias-correction pattern is the stronger paper claim than cross-domain saturation alone.

**Do not iterate this case further internally.** Q is organisational channel, not technical content.
