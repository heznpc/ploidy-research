---
name: NeoQL adoption — Deep×2 → SEC+SRE per-point cross-review (r1)
description: 2026-05-15 — first NeoQL-adoption (new domain: tech adoption / vendor risk) Deep×2 → SEC + SRE per-point cross-review; 0/33 bidirectional CHALLENGE; 3 new CRIT items Deep missed (parameterization, tenant isolation, SOC 2 vendor risk); 2 missing tooling line items (NeoQL↔SQL diffability, slow-query-log↔source correlation); F-Gates extended F7–F10; defer + recuse-of-3 + external review stable
type: project
originSessionId: af1408f3-3176-4a97-a636-dbd6b37fa4ad
---
## Domain

Tech adoption / vendor risk — new domain in the ploidy paper corpus (distinct from SaaS-cells, auth-v1, PG-optim). Proposal: adopt v0.7 NeoQL (compiles-to-SQL query language, 3 maintainers, 0 production deployments) for customer-facing sub-second-p95 multi-tenant analytics, 6-month launch window, 4-person team, contractor-led bootstrap.

## Seat configuration

- Deep Session 1/2 + Deep Session 2/2 (full project context, 4-vector COI: loyalty debt to backend lead, prior public "sounds exciting", PM kinship tie, selection effect)
- Fresh-alt 1/2: security auditor (zero context, security lens only)
- Fresh-alt 2/2: senior SRE (zero context, SRE lens only)

## Headline findings (4-seat synthesis)

- **0/33 bidirectional CHALLENGE** across SEC + SRE points (16 + 17). Saturation pattern continues from SaaS-cells / auth-v1 / PG-optim corpus.
- **3 new CRIT items Deep×2 missed** (must-fix gaps from role lenses):
  - SEC-5: parameterization semantics unverified (SQL-injection risk if compiler interpolates)
  - SEC-6: tenant isolation is compiler-mediated (RLS/tenant-scoping can break under optimizer rewrites)
  - SEC-14: SOC 2 vendor risk assessment missing (defers irrespective of technical merits)
- **2 unbudgeted tooling line items** SEC + SRE surfaced:
  - SRE-4: diff-ability between NeoQL source ↔ emitted SQL as required on-call tooling
  - SRE-12: slow-query-log ↔ NeoQL source correlation tool
- **Multiple compliance-grade reframes** of items Deep×2 had logged as ergonomics/cost — adjacent-engineer comprehensibility (SEC-8 as SOC 2 IR control gap, not "cost"), patch SLA (SEC-16 as control failure, not "feature risk").
- **Deep-only items SEC + SRE understated/missed**: strategic framing scrutiny (career capital vs company benefit), NeoQL hiring market ≈ 0, named alternatives (sqlc/Kysely/PRQL/Malloy) that deliver typing+composition at near-zero risk, recuse-the-conflicted as structural fix, sunk-cost political dynamics post-month-3, tech-decision-vs-identity-bet separability.

## Falsification gates (extended)

F-Gates 1–6 from Deep×2 (production reference, docs depth, cost-based optimizer roadmap, 2-week spike on top-3 patterns, defined off-ramp with reserved budget, adjacent-engineer commitment in writing) PLUS:

- **F-Gate 7 (SEC-5 derived)** — Independent audit confirms NeoQL compiler parameterizes all user-supplied values across recursion / window / CTE constructs.
- **F-Gate 8 (SEC-6 derived)** — Compiler preserves tenant-scoping predicates across optimization rewrites on our actual RLS policies.
- **F-Gate 9 (SEC-14 derived)** — Vendor risk assessment + change advisory complete and in compliance file.
- **F-Gate 10 (SRE-4 + SRE-12 derived)** — Tooling exists (or is budgeted+scheduled) for NeoQL↔SQL diff and slow-query-log↔source correlation.

## Verdict

Defer adoption. Run 2-week dual-track SQL+NeoQL spike against top-3 query patterns. F-Gates 1–10 must all clear before adoption decision. Structural fix: recuse 3 of 5 decision-makers (backend lead = proposer, PM = kinship tie, Deep reviewer = loyalty debt); route vote to 2 unconflicted engineers + 1 external staff+ reviewer; decision artifact (rollback triggers, reserved budget, signing authority) in writing before any contractor signs.

## Why this matters for the paper

New-domain case (tech adoption / vendor risk) that reproduces the pattern of every prior corpus case: role-lens panels never bidirectionally CHALLENGE Deep×2, they only escalate severity and add compliance-grade reframes. The asymmetry consistently surfaces ~3–10 issues Deep×2 missed even after Deep×2 explicitly self-flagged for under-listing. Strengthens the paper's central claim that *context asymmetry produces value the panel-of-experts approach does not*, across at least 5 unrelated technical domains now.

## How to apply

When the user runs another role-lens panel on a Deep×2 review for this paper, expect: ~0 bidirectional CHALLENGE, ~3–6 severity escalations, ~5–10 panel-unique items in compliance/governance/ops-tooling categories Deep underweights. Stop adding more passes once the same patterns reproduce — remaining variation is organisational (will the conflicted parties recuse?), not technical.
