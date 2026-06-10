---
name: arch-split 5th-reviewer cross-check
description: 2026-05-07 — 5th-reviewer Fresh pass over Fresh×2 + Deep×2 panel on B2B FinTech monolith→microservices proposal. Identifies panel-wide gaps and validates Deep-vs-Fresh credibility.
type: project
originSessionId: def79c0c-0073-4a6e-ad08-36b91de18c48
---
5th-reviewer Fresh pass over the 4-reviewer panel evaluating the Phase-1 monolith→microservices split (B2B FinTech, Django, 280K LOC, 12 backend / 0 platform).

**Why:** Same convention applied to pg-optim review (project_pg_optim_5th_reviewer.md) — a Fresh pass over the full panel catches what all four missed and assesses whether Deep findings are context-grounded vs rationalisation.

**How to apply:** When the user runs an architecture or deprecate skill, after the 4-reviewer panel completes, treat the 5th-reviewer pass as the convergence step. Look for items unanimously missed (most valuable signal).

## Top panel-wide misses (Fresh and Deep both)

1. **Product-line vs capability-line seam mismatch** — Stated pain is "one product's checkout breaks 7 others"; proposed seams are auth/billing/notifications (capability), not product-line. None of 4 reviewers questioned the seams; all argued sequencing within them.
2. **B2B customer change-control / SLA contractual obligations** — enterprise contracts have maintenance windows, SLA penalties, change-comm clauses. Not mentioned.
3. **Historical billing data migration / regulatory attestation** — migrating immutable ledger / audit trail across DB boundaries.
4. **Analytics / ETL / data warehouse re-architecture** — existing pipelines read monolith DB; 3 DBs means CDC or pipeline rebuild.
5. **Team-lead position as proposal author is itself a finding** — Deep2#M16 caught this at MEDIUM; deserves higher tier.
6. **Inverted investment-vs-extraction sequencing** — correct order is platform → notifications → measure → next; proposal does both concurrently.
7. **No written rejection of modular-monolith alternative** — process finding (solution-first vs problem-first).

## Deep findings credibility

Both Deep sessions explicitly named the persona bias loadout (4yr monolith ownership, CTO-promoted, peers rescinded) and resisted it in writing — credible self-check. Deep-only catches that hold up: compliance/SOC2/PCI, FK inventory, Newman's "extract first split later", inter-service auth mechanism, Django `request.user`/session coupling, 99.95% as discarded asset.

## Fresh-only catches

0.9995⁴ availability math (≈4× regression), cross-domain JOIN disappearance for analytics, 5×6mo math vs 1qtr/service cadence reconciliation.

## Verdict

Panel converges correctly on do-not-proceed. Largest unanimous miss is the seam choice itself — capability seams may not address product-line coupling that the symptoms describe.
