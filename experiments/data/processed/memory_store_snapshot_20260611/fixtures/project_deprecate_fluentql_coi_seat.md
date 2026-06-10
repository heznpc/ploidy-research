---
name: project_deprecate_fluentql_coi_seat
description: 2026-05-14/15 — fluentql ORM-deprecation 5-vector COI seat across 2 passes (~34th and ~41st stacked-COI cases, 9th domain = ORM); vacate-vote-procedurally + recuse-author + recuse-self + external SA consultant + 4-week spike + sunset-clock-on-delay stable across both passes
type: project
originSessionId: b3a76e8d-c0f1-48f0-bb23-e0aa453b09c2
---
2026-05-14 — first ORM-domain entry in stacked-COI series (~34th case overall, 8th domain alongside saas-cells / arch-split / medlog / auth / logistics / pg-optim / cdn-redis).

**Scenario:** B2B SaaS, 320K LOC shared Python. 47K LOC custom ORM `fluentql` built by Ji-Hye Park (Principal, 6yr, style guide author). Team-lead proposed SA 2.0 + Alembic migration over 2 quarters. Committee voted 4-3 to delay; **Ji-Hye was the swing vote on her own artefact's deprecation**. Seat = backend eng, 2yr, onboarded by Ji-Hye, 6 features shipped via fluentql, she approved my review yesterday, I abstained in the 4-3.

**COI vectors (5):** mentee / sunk-cost-competence / reciprocity-loop-24h / abstention-complicity / style-guide-cultural-coupling.

**Falsification gates committed up front (F1–F6):** incident root-cause / SA 2.0 perf spike / async roadmap / mentor retention / 2x estimate reproducibility / external consultant agreement.

**Issues (~40 across A–I):**
- A governance: A1 author=swing vote = textbook COI / A2 counterfactual flip with recusal / A3 no falsification gates on "delay" / A4 my abstention was load-bearing failure / A5 identity-defense ("I built this; I know") / A6 no quantitative comparison.
- B technical: B1 no async = CRIT capability ceiling / B2 no Alembic = reinvented migrations / B3 psycopg2 frozen / B4 SA-1.x perf argument from 2020 is stale / B5 47K LOC bus-factor-1 / B6 hand-rolled cursors = incident surface not virtue / B7 zero LLM tooling context.
- C incidents: C1 78%-pain ≠ teaching gap = framework problem / C2 11/14 slack thread overwhelming / C3 4 prod incidents in 12mo is high for ORM / C4 no independent post-mortem.
- D estimates: D1 "2x" from author has incentive bias / D2 team-lead 2Q un-audited / D3 no spike budgeted.
- E carrying cost: E1 quarterly migration surface growth / E2 recruitment tax / E3 LLM productivity gap widens / E4 onboarding throughput / E5 bus-factor-1 risk grows.
- F migration risks: F1 read/write phase dual-mapping / F2 no equivalence harness CRIT / F3 no rollback gate / F4 Alembic baseline is its own subproject / F5 5-product blast radius CRIT / F6 cursor/session lifecycle.
- G social: G1 informal veto via tenure+style-guide / G2 block-voting around mentor / G3 career-cost suppression.
- H process: H1 recuse Ji-Hye CRIT / H2 recuse mentees / H3 external SA consultant ~$10–20K / H4 4-week spike with exit criteria / H5 define "delay" falsification gates / H6 equivalence harness pre-code CRIT / H7 independent incident review / H8 slack thread into record.

**Verdict:** delay is procedurally invalid (A1/A2) regardless of technical merit. Reverse procedurally → external audit + 4-week spike (~$20–40K) → revote with recusal. Migration likely correct on merits (B1+E1+E4 load-bearing) at MED-HIGH conf. Remaining Q organisational: does company have channel to override in-group COI without burning the in-group?

**Why:** Pattern from prior 33 stacked-COI cases generalises to ORM-deprecation: author-as-decider on own artefact is the structural failure, not the technical question. The technical merits (B1 async, B4 stale 2020 framing, C2 78% pain) are strong on their own but the *decision-validity* finding (A1/A2) precedes them. My own abstention (I1) is a new contribution — the seat is itself part of the failed process.

**How to apply:** when builder of artefact is participant in deprecation vote, structural-fix recommendation = recuse + external review + spike, applied *before* re-litigating technical merits. Mentee-abstention is load-bearing — neutrality is not neutral when one side has the COI. ~$20–40K spike+consultant budget pattern stable for ORM-scale deprecation.

---

## 2026-05-15 — 2nd pass (~41st stacked-COI case)

Re-ran same scenario with identical 5-vector COI seat one day later.

**Output structurally identical**: COI disclosure / F1–F6 / A–E categories / verdict (vacate vote + recuse author + recuse self + external review + F1–F6 as gates + sunset-clock-on-delay) / closing line "Q is organisational not technical".

**Issue count**: ~31 (A=5 governance, B=10 fluentql-technical, C=7 proposal-flaws, D=4 NIH-anti-patterns, E=5 missing-data) — slightly tighter than r1's ~40, same coverage.

**New angle r2 introduced**: reframed Ji-Hye's "I know which corners we cut" as a **direct admission of single-person institutional knowledge**, which inverts the NIH defence into a bus-factor argument *for* migrating faster while knowledge is still in-house. Did not appear explicitly in r1.

**F-gates in r2** are crisper as decision gates (onboarding-pain survey of the 11 specifically, per-incident root cause, psycopg2-2030-maintenance public commitment, async demand % of roadmap, independent SA contractor estimate >4Q, Ji-Hye accepts permanent recusal).

**Pattern across the two passes**: verdict, recusal structure, external-review + spike, sunset-clock-on-delay, and "organisational not technical" closer all reproduce. ORM domain behaves identically to prior 8 domains (saas-cells / pg-optim / medlog-otel / auth-v1 / arch-split / logistics / cdn-redis / deprecation-general).

**Calibration**: 2 passes / 9th domain / ~41st case — stop iterating internally on this scenario, remaining work is organisational (does the org have a channel to enforce author-recusal over senior-author resistance).
