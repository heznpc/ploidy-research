---
name: NeoQL role-lens cross-review (Deep×2 → SEC + SRE)
description: 2026-05-15 — per-point cross-review of NeoQL adoption COI seat by SEC auditor + SRE; 0 bidirectional CHALLENGE, ~14 SYNTHESIZE adoptions, 3 new CRIT (compiler audit, parameterization contract, tenant-isolation predicate handling), F-gates extended to F1–F9; verdict shape stable
type: project
originSessionId: aefd0854-aa26-47fb-8e7d-c4b181608ba9
---
# NeoQL role-lens cross-review (Deep×2 → SEC + SRE)

**Case:** ~65th stacked cross-review case in this project; ~12th pass on the NeoQL COI seat specifically.

## Headline

- **0 bidirectional CHALLENGE.** Same pattern as auth-v1 and SaaS-cells panels.
- **~14 SYNTHESIZE adoptions** from role-lens reviewers.
- **3 items promoted to new CRIT:**
  - SEC-2 (compiler is the SQLi defense — no audit on v0.7)
  - SEC-3 (parameterization contract undocumented)
  - SEC-7 (single-pass optimizer can drop tenant-isolation predicates under reordering/merging)
- **F-gates extended F1–F6 → F1–F9** (added: tenant-isolation conformance, parameterization contract test suite, SQL↔NeoQL source mapping).
- **Verdict unchanged:** defer NeoQL; default Postgres + sqlc/Kysely/Drizzle + repository; recuse-of-3 + external unconflicted reviewer with veto authority; 2-week time-boxed spike as cheapest unblocker.

## Deep-only items panels missed (10)

1. COI structure (3-of-4 hired by proposer; PM connection; senior dissenter 4 COI vectors)
2. Recuse-of-3 + external staff/principal with veto authority
3. D4 / proposer-benefits-asymmetrically named in writing
4. F-gates committed BEFORE issue list (methodology, not content)
5. 2-week spike on 5 hardest PRD queries, voted on by unconflicted external
6. Saturation meta-observation (~12th pass on identical seat)
7. Concrete alternative stack named (Postgres + sqlc/Kysely/Drizzle + repo)
8. "Shaping the language" framing as sunk-cost generator / lock-in mechanism
9. PM personal connection as vote-counting risk
10. Routing: external IC / board memo, not internal re-litigation

## Calibration

Stop iterating internally. Remaining question is organisational channel (who chairs the decision), not technical content. Signal is saturated across now ~65 stacked cases / 10 domains.
