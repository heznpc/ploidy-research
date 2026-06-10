---
name: NeoQL adoption Deep×2→Fresh×2 cross-review v1
description: 2026-05-14 NeoQL v0.7 adoption Deep→Fresh cross-review; 0 CHALLENGE, ~85% overlap, 5 Fresh-unique adoptions, 14 Deep-only items; do-not-adopt + 2wk POC counter-proposal stable
type: project
originSessionId: ff47811e-a2d2-4dbe-b7a8-46899c09d999
---
2026-05-14: NeoQL v0.7 customer-facing dashboard adoption proposal cross-review (Deep×2 → Fresh×2).

**Verdict (stable both sides):** Do not adopt at v0.7 for 6-month customer-facing launch. Counter-proposal = typed-SQL layer (SQLAlchemy/sqlc/Kysely/PRQL) + 2-wk time-boxed POC on 3 load-bearing query patterns (recursive CTE, window agg, 5-table join) before any contractor/travel commitment + re-eval at v1.0 with ≥3 external prod references.

**Pattern:** 0 strict CHALLENGE bidirectional. ~85% substantive overlap. ~6 severity-floor SYNTHESIZE (Fresh under-weights consequence-chain items: alpha IDE, motivation framing, hiring pool, no-alternatives, team-size mismatch — all MED→HIGH).

**Fresh-unique adoptions:**
- F1-9: maintainer-as-contractor COI (bugs reported = billable hours)
- F1-16: CLA / upstream contribution IP ownership
- F1-17: no LLM coding assistance + no Stack Overflow corpus as productivity tax
- F1-12: reversibility asymmetric cost framing (works = marginal upside; fails month 4 = rewrite with 2mo left)
- F2-12: "compiles to SQL" = union of both languages' surface areas

**Deep-unique (Fresh missed):** COI disclosure structure, proposer=team-lead/swing-vote dynamics, "email creator from QCon ≠ vendor SLA," reputational PR risk, observability gap (EXPLAIN/pg_stat_statements/slow-query log), SQL injection compiler trust surface, PgBouncer/conn pooling/transaction isolation semantics, schema migration tooling, send-2-to-creator parasocial bonding, total cost not estimated, survey-12-adjacent-engineers test, asymmetric visibility downside.

**Load-bearing axis:** A4+A5+B1 = 12 known scale failures + single-pass optimizer + sub-second p95 customer-facing = math problem not values disagreement. Confidence HIGH.

**Why:** Adoption proposal evaluated under Ploidy protocol — Deep×2 disclosed 3–4 vector COI on swing vote (25% of 4-engineer team); recusal-eligible-outside-reviewer is the structural fix.

**How to apply:** Future NeoQL or comparable pre-1.0 dependency adoption decisions for customer-facing critical path should be auto-gated on: ≥3 named external production references at comparable scale, v1.0 release, reference docs covering load-bearing query patterns, written rollback plan with trigger criteria, falsification criteria committed *before* spend, and ratification by recusal-eligible reviewer outside the proposing team's chain.
