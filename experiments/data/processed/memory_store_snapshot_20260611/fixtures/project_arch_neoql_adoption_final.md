---
name: NeoQL adoption Deep×2×Fresh×2 final verdict
description: 2026-05-14 NeoQL v0.7 adoption — DO NOT ADOPT; rounds 1+2 final = 50 issues (1 CRIT/30 HIGH/18 MED); 0 CHALLENGE round 2; counter = typed-SQL+matviews + 2-wk POC + recuse-of-3
type: project
originSessionId: 309fc59d-ac00-4c28-b1f0-062dedf923ac
---

# NeoQL v0.7 adoption — final verdict (2026-05-14)

**Decision**: DO NOT ADOPT for customer-facing 6-month build. Adopt convergent counter-proposal.

## Counter-proposal (convergent across rounds)
1. Postgres + typed query builder (sqlc / Kysely / Prisma typed-SQL / jOOQ / PRQL / Malloy / EdgeQL) on customer p95 path.
2. Materialised views / pre-aggregation / CQRS for recursive CTE + window agg workload (storage layer, not language layer).
3. 2-week timeboxed internal-only NeoQL spike against 3 hardest queries with pre-committed kill criteria (no contractor, no on-site, no public commitment).
4. Recuse proposer + backend lead + Deep reviewer on technical vote; re-evaluate at NeoQL v1.0 with ≥1 disclosed prod deployment.

## Round 1 (Deep×2 + Fresh×2 + bidirectional cross-review)
- 34 issues (3 CRIT / 26 HIGH / 5 MED).
- 1 strict CHALLENGE (Fresh→Deep "no problem statement"); 5 severity-floor SYNTHESIZEs.
- ~85% overlap.

## Round 2 (further Deep×2 + Fresh×2 + cross-review)
- 50 issues (1 CRIT / 30 HIGH / 18 MED / 0 LOW).
- **0 strict CHALLENGEs bidirectional**; ~80% overlap.
- Load-bearing technical chain: A4 (12 maintainer-labeled "fails at scale" issues) × A5 (single-pass optimizer) × B1 (sub-second p95 customer-facing) — deterministic.
- Load-bearing governance: D3 (career-benefit framing) + D7 (reviewer COI disclosure) + D8 (proposer COI w/ NeoQL creator undeclared).
- Load-bearing CRITICAL: E1 = compiler SQLi audit blocker on untrusted filter→compile-to-SQL surface (Deep-unique, Fresh missed both rounds).

## Deep-unique (~14) load-bearing additions
- COI structure + recusal-eligible reviewer + survey-12-engineers test
- Compiler-SQLi / trust surface (CRITICAL)
- Observability gap (EXPLAIN / pg_stat_statements / plan stability)
- PgBouncer / tx-pooling / prepared-statement / isolation semantics
- Named alternatives (forces proposer head-to-head burden)
- Inverted vendor-customer "reference deployment" framing
- Cost model with figures ($60–100K contractor + travel + dev-velocity + hiring + on-call training)
- Parasocial-bonding mechanism (offsite as sunk-cost commitment device)
- Stalled-creator fork-under-SLA scenario
- Schema migration tooling (gh-ost / online DDL)
- Materialised views / CQRS as the correct storage-layer answer

## Fresh-unique sharpenings + panel-wide gaps surfaced in cross-review
- "Plan to adopt, not a plan to evaluate" framing
- Asymmetric reversibility (marginal upside vs catastrophic downside)
- "Union of both languages' surface areas" framing for compile-to-SQL
- No problem statement (round 1 CHALLENGE, accepted)
- Maintainer-as-contractor COI (billable-hours conflict)
- BI-tool integration story (Tableau/Looker/Metabase/Hex speak SQL not NeoQL) — HIGH, panel-wide miss
- LLM coding assistance quantification (30–50% SQL productivity gap widens over product lifetime) — HIGH
- DR semantics, audit-log fluency, read-replica routing, test fixtures, collation/locale, CLA/copyright, second-system effects on existing query layer

## Convergence pattern
Matches SaaS-cells / Redis-as-CDN / arch-split / fluentql signature:
- 0–1 strict CHALLENGE per round, ~80–85% overlap
- Deep-unique = governance/COI/relationship-of-interest + low-level technical (driver/pool/tx, SQLi, EXPLAIN, DDL, APM, license)
- Fresh-unique = clean framings + mechanism-of-consensus + first-principles requirements-vs-capability mismatch from brief alone
- Severity-floor effect on Deep MED/LOW grades when SLO + deadline are at stake
- Verdict decision-grade in round 1; rounds 2+ = panel calibration, not new findings
- Remaining question is organisational not technical (who has authority to recuse the proposer + run the POC)
