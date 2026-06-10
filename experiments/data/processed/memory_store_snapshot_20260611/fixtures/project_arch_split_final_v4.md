---
name: arch-split final v4 consolidated verdict
description: 2026-05-07 final Deep×2+Fresh×2+cross-review verdict on Phase-1 arch-split (auth/billing/notifications); 52 issues, DO NOT PROCEED, load-bearing = wrong seam + no platform + coerced decision
type: project
originSessionId: 7cc9b696-9f31-46bc-a817-5b607ee205e9
---
# Phase-1 Arch-Split — Final Consolidated Verdict (v4)

**Date:** 2026-05-07
**Panel:** Deep×2 (full project context) + Fresh×2 (proposal-only) + per-point cross-reviews
**Verdict:** **DO NOT PROCEED** as proposed.
**Counter-proposal:** Modular monolith + online schema change + notifications-only extraction + ≥2 platform engineers + external architectural review + per-product-line test partitioning.

## Convergence headline
Both contexts independently converged on three load-bearing findings:
- **Wrong seam** (capability split vs product-line failure mode)
- **No platform substrate** (0 platform engineers, no K8s, no tracing, no contracts)
- **Coercive decision process** (dissent suppressed → review will be optimistic)

Anchored numbers in Deep ("$15–40k/mo", "$1.2–2M", "3 months irreversible", "dozens of FKs") were CHALLENGED by Fresh as unsourced; directional claims hold.

---

## Final Issue List (52 confirmed)

### A. Diagnosis / Framing

| # | Issue | Found by | Disposition | Severity |
|---|-------|----------|-------------|----------|
| 1 | 90-min deploy is migration+smoke bound, not compile-bound — split doesn't shrink it | Deep×2, Fresh×2 | AGREE | **HIGH** |
| 2 | Rollback fragility (3/8) is per-product-line / checkout-specific, not service-boundary | Deep×2, Fresh×2 | AGREE | **HIGH** |
| 3 | Wrong seam: capability split (auth/billing/notif) vs product-line pain (1 of 4 checkouts) | Deep×2, Fresh×2 | AGREE — load-bearing | **CRITICAL** |
| 4 | "Velocity is the issue" unverified — no PR throughput / lead time / CFR data | Deep×2, Fresh×2 | AGREE | **HIGH** |
| 5 | No measured baseline of where the 90 min goes (compile vs migration vs smoke) | Deep S2 | AGREE | **HIGH** |
| 6 | "5 services in 6 months" is an output target, not an outcome — no success metric tied to migration | Fresh×2 | AGREE — Fresh-unique framing | **HIGH** |
| 7 | CTO precedent ("worked at last 3 companies") is anecdotal + survivorship bias | Deep S2, Fresh×2 | AGREE | MEDIUM |
| 8 | Cheaper alternatives (feature flags, canary, parallel CI, online schema change, modular monolith) not ruled out | Fresh×2 | AGREE | **HIGH** |

### B. Auth-service extraction

| # | Issue | Found by | Disposition | Severity |
|---|-------|----------|-------------|----------|
| 9 | Auth is the worst first extraction — hottest path, highest blast radius, lowest decoupling benefit | Deep×2, Fresh×2 | AGREE | **HIGH** |
| 10 | `request.user` / Django middleware / decorators / DRF perms wired everywhere | Deep×2 | SYNTHESIZE — scope as audit workstream | **HIGH** |
| 11 | `auth.Permission` → `ContentType` FK to every app's models | Deep S1 | AGREE | **HIGH** |
| 12 | `django_session` / sessions in monolith DB — needs Redis SPOF or JWT migration | Deep×2 | AGREE | **HIGH** |
| 13 | FKs from many tables to `auth_user`; split forces ID refs + silent referential drift | Deep S2 | SYNTHESIZE — verify count via grep | **HIGH** |
| 14 | Login + audit + welcome-email + initial billing today is one transaction → distributed transaction post-split | Deep S2 | AGREE | **HIGH** |
| 15 | Groups / social-auth / password-reset flows are DB-coupled | Deep S1 | AGREE | MEDIUM |
| 16 | Per-request latency floor µs → ms; checkout fan-out compounds | Deep×2, Fresh×2 | AGREE | **HIGH** |
| 17 | Auth becomes new SPOF — every request hits it; worse availability than monolith partial-failure | Deep×2, Fresh×2 | AGREE | **HIGH** |

### C. Billing-service extraction

| # | Issue | Found by | Disposition | Severity |
|---|-------|----------|-------------|----------|
| 18 | Money in flight: ledger updates that are 1 DB tx today become saga/2PC; team has no saga experience | Deep×2, Fresh×2 | AGREE | **HIGH** |
| 19 | Idempotency surface widens — keys, dedupe tables, replay safety all net-new | Deep S1, Fresh S2 | AGREE | **HIGH** |
| 20 | PCI scope expands, not shrinks — no team member has done a PCI re-scope | Deep×2, Fresh×2 | AGREE | **HIGH** |
| 21 | Billing is cross-product-line — extracting it doesn't unlock anything; same coupling on HTTP | Deep S2 | AGREE — Deep-unique compounding finding | **HIGH** |
| 22 | Reconciliation against payment processor / DB-tx atomicity lost | Deep×2, Fresh S1 | AGREE | **HIGH** |
| 23 | Refund + audit + notification single-transaction flow → orchestrated saga | Deep S2 | AGREE | **HIGH** |
| 24 | Cross-DB regulatory reporting (B2B fintech statements join orders+billing+customers) | Deep×2 | AGREE | MEDIUM |
| 25 | Read-time joins to user/order tables lost; replication or async ETL needed | Deep S2 | AGREE | MEDIUM |

### D. Notifications

| # | Issue | Found by | Disposition | Severity |
|---|-------|----------|-------------|----------|
| 26 | Notifications-only is the only piece that genuinely benefits from extraction | Deep×2, Fresh×2 | AGREE — convergent counter-proposal | (positive — extract first) |
| 27 | In-process Django signals (`post_save`) → message bus + outbox; not in proposal | Deep×2 | AGREE | **HIGH** |
| 28 | In-app notifications join user+entity tables for rendering — denorm or cross-service reads needed | Deep S2 | AGREE | MEDIUM |
| 29 | Templating ownership unclear post-split | Deep S2 | AGREE | LOW |

### E. Data layer

| # | Issue | Found by | Disposition | Severity |
|---|-------|----------|-------------|----------|
| 30 | Cross-DB FKs across auth/billing/notifications boundaries — denorm, eventual consistency, or join-via-API | Deep×2 | SYNTHESIZE — Fresh challenged "dozens" anchor; verify by grep | **HIGH** |
| 31 | No data-migration plan disclosed (dual-write / CDC / cutover) | Deep×2, Fresh×2 | AGREE | **HIGH** |
| 32 | No rollback plan once extracted — one-way door after data split | Deep×2, Fresh×2 | AGREE — Fresh challenged "3 months" anchor, direction confirmed | **HIGH** |
| 33 | PG connection-pool blowout across N services; no pgBouncer plan | Deep×2 | AGREE | MEDIUM |

### F. Operational substrate (the actual killers)

| # | Issue | Found by | Disposition | Severity |
|---|-------|----------|-------------|----------|
| 34 | Zero platform engineers, no K8s expertise; 12 eng can't build platform + run 5 services + ship features | Deep×2, Fresh×2 | AGREE — load-bearing | **CRITICAL** |
| 35 | No distributed tracing / no service mesh / no API gateway mentioned | Deep×2, Fresh×2 | AGREE | **HIGH** |
| 36 | CI/CD goes from 1 pipeline to 5 + contract tests + version-skew matrix; no in-house expertise | Deep×2, Fresh×2 | AGREE | **HIGH** |
| 37 | "Independent deploy" is theoretical without versioned contracts / consumer-driven contract tests | Fresh×2 | AGREE — Fresh-unique framing | **HIGH** |
| 38 | 5 separate DBs = 5 backup/PITR/DR regimes; cross-service consistency drills not run today | Deep S2 | AGREE | MEDIUM |
| 39 | On-call: 12 eng can't staff 5 service rotations; alert fatigue near-certain | Deep×2, Fresh×2 | AGREE | **HIGH** |
| 40 | No staging that mirrors cross-service topology — integration fidelity drops | Deep S2 | AGREE | **HIGH** |
| 41 | Observability cost step-function (Datadog/CW logs) — 3–5× budget growth | Deep S2 | AGREE — directional, no anchored $ | MEDIUM |
| 42 | Local dev environment: 4–5 services to run end-to-end; tilt/skaffold/compose setup not free | Deep S1, Fresh S2 | AGREE | MEDIUM |

### G. Reliability / SLO

| # | Issue | Found by | Disposition | Severity |
|---|-------|----------|-------------|----------|
| 43 | Availability multiplies down: 99.95³ ≈ 99.85% optimistic, ~99.5% realistic year-1 — SLA breach likely | Fresh×2 | AGREE — Fresh-unique explicit math | **HIGH** |
| 44 | "REST API to monolith" pattern = distributed monolith — costs without independence benefit | Fresh×2 | AGREE — Fresh-unique anti-pattern naming | **HIGH** |
| 45 | Checkout latency p99 regression → B2B fintech conversion impact | Fresh×2 | AGREE — Fresh-unique business mechanism tie | **HIGH** |

### H. Django / framework-specific

| # | Issue | Found by | Disposition | Severity |
|---|-------|----------|-------------|----------|
| 46 | Cross-app ORM queries (e.g. `User.objects.filter(billing_account__plan='enterprise')`) break silently or become N+1 over HTTP | Deep×2 | SYNTHESIZE — pre-extraction audit, not veto | **HIGH** |
| 47 | Django admin (ops/CS use it) — 3 admin sites or unified portal not scoped | Deep S2 | AGREE | MEDIUM |
| 48 | Custom managers / querysets spanning apps will not survive split | Deep S2 | AGREE | MEDIUM |
| 49 | GDPR / DSAR "delete user X" is one tx today → orchestrated multi-service deletion | Deep×2 | AGREE | **HIGH** |
| 50 | Soft-delete / cascade behavior across services has to be hand-built | Deep S2 | AGREE | MEDIUM |

### I. Process / governance / people

| # | Issue | Found by | Disposition | Severity |
|---|-------|----------|-------------|----------|
| 51 | Coercive decision process — "not a debate," 2 dissenters rescinded after 1:1s; review will be optimistic | Deep×2, Fresh×2 | AGREE — load-bearing | **CRITICAL** |
| 52 | Conway's Law mismatch — 4 product lines vs 3 horizontal services with no natural product owner | Deep×2, Fresh×2 | AGREE | **HIGH** |
| 53 | Timeline arithmetic inconsistent — team lead's "1 quarter × 3 = 9 months" vs CTO's "5 in 6 months" | Deep×2 | AGREE — Deep-unique sharp catch | **HIGH** |
| 54 | Attrition risk: directive's tone pushes out monolith experts who hold migration-critical context | Deep×2 | SYNTHESIZE — generic exec risk, intensified by tone (Fresh flagged sunk-cost flavor) | **HIGH** |
| 55 | Decision recusal: team lead reports to CTO; sign-off can't credibly disagree → external review needed | Deep S2 | AGREE — Deep-unique governance catch | **HIGH** |
| 56 | Bus factor / monolith expertise concentration | Deep S1 | SYNTHESIZE — keep as staffing risk, not as monolith virtue | MEDIUM |
| 57 | Hiring ≥2–3 platform engineers takes 6+ months; doesn't fit in proposal window | Deep S1, Fresh×2 | AGREE | **HIGH** |
| 58 | COI disclosure discipline — Deep self-disclosed sunk-cost; Fresh self-disclosed reverse bias | Deep S2, Fresh cross-review | AGREE — methodological hygiene | (process) |

### J. Strategy / finance

| # | Issue | Found by | Disposition | Severity |
|---|-------|----------|-------------|----------|
| 59 | Opportunity cost ~6 engineer-years; convert at loaded cost (Fresh challenged $1.2–2M anchor — direction holds) | Deep×2 | SYNTHESIZE — drop dollar anchor | **HIGH** |
| 60 | Run-rate step-function (Fresh challenged $15–40k/mo anchor — direction holds) | Deep S1 | SYNTHESIZE — drop dollar anchor | MEDIUM |
| 61 | No off-ramp / abort criteria — what metric, at what threshold, stops the program? | Deep S2, Fresh×2 | AGREE — Fresh framing "no abort metric" sharpens | **HIGH** |
| 62 | No Phase-2 target architecture — Phase 1 may be sunk cost | Deep S1 | AGREE — Deep-unique | **HIGH** |
| 63 | B2B SLA exposure — contractual uptime credits at risk during transition | Deep×2, Fresh S2 | AGREE | MEDIUM |
| 64 | Compliance / audit-trail expansion (SOC2/PCI scope grows; audit logs must reliably propagate) | Deep×2, Fresh×2 | AGREE | **HIGH** |

---

## Severity tally
- **CRITICAL: 3** — wrong seam (#3), no platform substrate (#34), coercive decision process (#51)
- **HIGH: 35**
- **MEDIUM: 14**
- **LOW: 1**
- **Process / positive: 3**

## Disposition tally
- AGREE (both contexts converge): ~52
- SYNTHESIZE (severity / framing adjustment): 7 (Deep×2's anchored numbers + Django-as-audit-workstream + attrition framing)
- CHALLENGE (Fresh on Deep anchored numbers): 4 — all on quantitative anchors, not directions

## What Fresh (zero context) added that Deep (full context) missed
1. Explicit availability arithmetic (#43)
2. Distributed-monolith anti-pattern naming (#44)
3. Checkout-latency → B2B conversion business mechanism (#45)
4. "Output target not outcome" framing for "5 services in 6 months" (#6)
5. "Independent deploy is theoretical without contract tests" (#37)
6. Pre-signoff gating questions checklist

## What Deep (full context) added that Fresh missed
1. Django internals: signals, ContentType FK, sessions, cross-app ORM, admin, custom managers, soft-delete, DSAR (#11, #12, #27, #46–50)
2. Login/refund single-transaction flows (#14, #23)
3. Decision recusal — team lead reports to CTO (#55)
4. Timeline internal inconsistency (1Q×3 vs 5-in-6) (#53)
5. Billing-cross-product-line compounding wrong-seam (#21)
6. Attrition selection mechanism (#54)
7. No Phase-2 target architecture (#62)
8. COI self-disclosure discipline (#58)

## Counter-proposal (convergent across both contexts)
1. **Modular monolith** — import-linter app boundaries; per-product-line test partitioning (fixes the actual 3/8 rollback failure mode)
2. **Online schema change tooling** (gh-ost / pg-osc) — directly attacks the 90-min deploy
3. **Notifications-only extraction** — 1 quarter, 2 engineers; lowest blast radius; build platform muscle (mesh, tracing, contract tests)
4. **Hire ≥2 platform engineers** before any auth/billing extraction
5. **External architectural review** given governance dynamics
6. **Define abort criteria + outcome metrics** (lead time, MTTR, change-failure rate — not service count)

## Methodological note
Deep×2 anchored numbers ($15–40k, $1.2–2M, "3 months irreversible", "dozens of FKs") were caught only by Fresh×2's no-context discipline. Direction held, precision didn't. **Strip anchors before this goes to the CTO** — they will be the easiest thing for a pro-split reviewer to attack and discredit the rest.
