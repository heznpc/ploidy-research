---
name: fluentql_final_v6
description: 2026-05-07 Round-6 final fluentql deprecation verdict — 53 issues (3 CRIT/27 HIGH/18 MED/5 LOW); 0 CHALLENGE bidirectional 5 rounds running; recommendation (recuse + harden + re-vote, Alembic-first as wedge) stable; calibration = stop iterating
type: project
originSessionId: 8af3c5d3-f3ee-4ced-9725-706f44a8150f
---
# fluentql migration delay — round-6 final consolidated verdict (2026-05-07)

**Decision under review:** 4-3 committee vote to delay fluentql→SQLAlchemy migration; author of fluentql cast the deciding vote against deprecation.

**Verdict:** SET ASIDE on process grounds. Re-vote with author recused. If technical merits re-litigated, migration is probably correct, but proposal also needs hardening (POC, off-ramp, dual-stack plan). **Highest-EV move regardless of ORM outcome: Alembic-first** (no author-COI hook attached).

**Convergence:** 0 strict CHALLENGEs bidirectional across 5 rounds running. Recommendation stable.

---

## Final Issue Matrix (53 confirmed)

### Process / Governance (12)

| # | Issue | Found by | Status | Severity |
|---|---|---|---|---|
| G1 | COI on swing vote — author voted on deprecation of own creation | Both (4/4) | AGREED | **CRITICAL** |
| G2 | No formal recusal policy in committee charter (structural defect) | Deep (1/2) | AGREED in cross | HIGH |
| G3 | Abstention load-bearing; 3 abstentions including reviewer's own | Deep (1/2) | SYNTHESIZED — disclosure correct, *causal* claim conditional on counterfactual | MEDIUM |
| G4 | Decision rests on author testimony, not data (no RCAs, no benchmarks, no funnel) | Both (4/4) | AGREED | HIGH |
| G5 | No reverse off-ramp on "delay" — no revisit trigger, no metric | Deep (1/2) | AGREED — strongest single fix to delay outcome short of recusal | HIGH |
| G6 | No committee-composition disclosure by fluentql authorship | Deep (1/2) | AGREED | MEDIUM |
| G7 | Chilling effect on future proposers re Principal-authored systems | Deep (1/2) | SYNTHESIZED — plausible but not directly observable from minutes; MED until corroborated | MEDIUM |
| G8 | Code-review authority asymmetry — voters report through author | Deep (2/2) | AGREED — reinforces recusal independent of vote count | HIGH |
| G9 | Argument from authorship ("I built this"), not engagement with data | Fresh (1/2) | AGREED | HIGH |
| G10 | Rebuttal targets wrong baseline (2020 question vs 2026 question) | Fresh (1/2) | AGREED | HIGH |
| G11 | 4-3 split is unresolved-disagreement signal; "delay" preserves it | Fresh (1/2) | AGREED — separate defect from COI | MEDIUM |
| G12 | Reciprocity exposure (PR approved day before vote) on the abstaining seat | Deep (1/2) | AGREED — correct disclosure | HIGH |

### Substantive Errors in Author's Rebuttal (10)

| # | Issue | Found by | Status | Severity |
|---|---|---|---|---|
| R1 | "SQLA 1.x had performance issues" — stale; proposal is SA 2.0 | Both (3/4) | AGREED | HIGH |
| R2 | "Designed for our patterns 5 years ago" cuts toward re-evaluation, not against | Fresh (1/2) | AGREED | HIGH |
| R3 | "Incidents = users misunderstand DSL" is unfalsifiable AND framework-defect signal | Both (3/4) | AGREED | HIGH |
| R4 | "Teach fluentql better" has no metric, no timeline, no sunset | Both (4/4) | AGREED — falsifiability ratchet (≤3/14 in 2Q) is the right ask | HIGH |
| R5 | "47K LOC of working code" frames sunk cost as asset | Both (4/4) | AGREED | HIGH |
| R6 | "I know exactly which corners we cut" *supports* migration (bus factor) | Both (3/4) | AGREED — most precise judo move | HIGH |
| R7 | "2x longer than estimated" — no basis; estimator credibility caveat | Deep (1/2) | AGREED | MEDIUM |
| R8 | Symmetric estimate scrutiny missing — migrate-cost gets 2x, carry-cost gets 0x | Deep (1/2) | AGREED | HIGH |
| R9 | Asymmetric explanation: misuse never read as design failure (unfalsifiability tell) | Fresh cross (1) | AGREED — sharpening | HIGH |
| R10 | Sunk-cost framing of bespoke ORM as preserved asset | Both (3/4) | AGREED | HIGH |

### Status-Quo Technical Risk (11)

| # | Issue | Found by | Status | Severity |
|---|---|---|---|---|
| T1 | Bus factor of 1 on 47K LOC across 5 products | Both (4/4) | AGREED | **CRITICAL** |
| T2 | No async support — forward-looking ceiling for B2B SaaS | Both (4/4) | AGREED | HIGH |
| T3 | Custom migration tooling, no Alembic — single point for migration safety across 5 products | Both (4/4) | AGREED — highest-value/lowest-author-COI wedge | **CRITICAL** |
| T4 | 4 incidents/12 mo not steady-state, no declining trend | Both (3/4) | SYNTHESIZED — severity HIGH overstated absent MTTR/blast-radius data | MEDIUM |
| T5 | Hiring/retention tax — 11/14 onboarding pain affects funnel + attrition | Both (4/4) | AGREED | HIGH |
| T6 | SQL-injection surface unaudited — custom escaping, no community review | Deep (1/2) | SYNTHESIZED — frame as *unaudited*, not *known weaker*; no vuln cited | MEDIUM |
| T7 | No static analysis / typing / IDE / lint — productivity drag | Deep (1/2) | AGREED | MEDIUM |
| T8 | psycopg2 (not psycopg3) — maintenance mode, eventual EoL | Both (2/4) | AGREED — calendar exposure independent of ORM debate | MEDIUM |
| T9 | No upstream feature flow (window fns, JSON, CTEs, upsert) | Deep (1/2) | AGREED | MEDIUM |
| T10 | Custom DSL fragments hiring — no transferable knowledge | Fresh (2/2) | AGREED | MEDIUM |
| T11 | Test coverage of fluentql itself unstated — *also* a stay cost | Fresh cross (1) | AGREED | MEDIUM |

### Migration-Plan Risks (10)

| # | Issue | Found by | Status | Severity |
|---|---|---|---|---|
| M1 | Dual-stack window for Phase-1 reads → Phase-2 writes — duration/ownership/rollback unspecified | Both (4/4) | AGREED | HIGH |
| M2 | Test-coverage prerequisite not stated — hidden phase-0 work | Both (4/4) | AGREED | HIGH |
| M3 | Extraction depth unknown — likely business logic mixed in | Deep (1/2) | SYNTHESIZED — frame as *risk requiring code-survey gate*, not *known to be deep* | MEDIUM |
| M4 | Connection-pool / transaction / session semantics differ silently | Deep (1/2) | AGREED — frequently underestimated | HIGH |
| M5 | 5-product blast radius / coordination cost unaddressed | Both (3/4) | AGREED — multi-product without sequence plan = CRIT-class plan defect | HIGH |
| M6 | No POC / time-boxed spike to validate 2-quarter estimate | Both (4/4) | AGREED — cleanest path to retire estimate dispute | HIGH |
| M7 | Alembic-first as smaller wedge with no author-COI hook | Deep (1/2) | AGREED — Fresh cross *elevated* to highest-EV move | HIGH |
| M8 | 2-quarter estimate likely optimistic | Both (3/4) | SYNTHESIZED — neither side has a basis; POC-derived number required | MEDIUM |
| M9 | No mapping of historical incidents → SA features that would prevent recurrence | Fresh (1/2) | AGREED — low-cost proposal hardening | LOW |
| M10 | Off-ramp from the migration itself unspecified (symmetric to G5) | Fresh cross (1) | AGREED | MEDIUM |

### Personal-Bias Disclosures (Deep self-disclosure) (4)

| # | Issue | Found by | Status | Severity |
|---|---|---|---|---|
| X1 | Reciprocity (PR approved day before vote) | Deep (1/2) | AGREED | HIGH |
| X2 | Self-justifying competence (fluentql skill = ROI on author's investment in reviewer) | Deep (1/2) | AGREED | HIGH |
| X3 | Power asymmetry (2 yr reviewer vs 6 yr Principal/style-guide author) | Deep (1/2) | AGREED | MEDIUM |
| X4 | Abstainer's own pain *is* part of the 11/14 signal author dismissed | Deep (1/2) | AGREED | HIGH |

### Fresh-Side Additions (panel-wide gaps) (10)

| # | Issue | Found by | Status | Severity |
|---|---|---|---|---|
| A1 | Customer/SLA exposure during migration — B2B contracts, no risk register / change-window plan | Fresh cross | NEW | HIGH |
| A2 | Compliance / audit asymmetry — SOC2/PCI/GDPR auditors flag custom DALs | Fresh cross | NEW | MEDIUM |
| A3 | Hiring-market externality — 5-yr fluentql skill has no portability (golden handcuffs) | Fresh cross | NEW | MEDIUM |
| A4 | Falsification protocol for "teach better" not hard-spec'd (instrument + threshold + auto-trigger in charter) | Fresh cross | NEW — sharpens R4 | HIGH |
| A5 | Alembic-first vote = COI diagnostic (artifact-specific vs change-resistant) | Fresh cross | NEW | MEDIUM |
| A6 | Documentation/knowledge externalization is COI-free ask, do now regardless | Fresh cross | NEW | LOW |
| A7 | RCA documents for the 4 incidents — existence itself decision-relevant | Fresh cross | NEW | MEDIUM |
| A8 | Proposer's own COI not symmetrically disclosed (visibility/promotion benefit) | Fresh cross | NEW | LOW |
| A9 | Strangler-fig / incremental coexistence path not evaluated in minutes | Fresh (1/2) | NEW | LOW |
| A10 | Minutes themselves under-document substantive discussion (brief-as-counter-evidence) | Fresh (1/2) | NEW | LOW |

---

## Severity rollup

| Severity | Count |
|---|---|
| **CRITICAL** | 3 (G1, T1, T3) |
| HIGH | 27 |
| MEDIUM | 18 |
| LOW | 5 |
| **Total** | **53** |

## Load-bearing chain

**G1** (COI swing vote) + **G5** (no off-ramp) + **R3 + R4 + R6** (rebuttal logic defects) + **T1 + T3** (bus factor + Alembic gap) + **M7** (Alembic-first wedge) + **A4** (falsification protocol) — accepting these forces re-vote with recusal AND determines the substance of the hardened proposal.

## Cross-round stability (5 rounds)

- Recommendation unchanged across 5 rounds: **recuse → harden plan → re-vote**
- Highest-EV move unchanged: **Alembic-first** (decoupled, no author-COI hook)
- Strict CHALLENGEs bidirectional: **0** across 5 rounds
- Systematic Fresh gap: severity-floor under-grading on consequence-chain items
- Systematic Deep gap: speculation-severity (extraction depth, SQLi framing) where Fresh correctly demanded evidence-grading
- **Calibration: stop iterating** — convergence stable, recommendation correct on the record presented

## Recommended next moves

1. **Vacate the delay vote** on process grounds (G1, G5, G8).
2. **Re-vote with author recused**; require committee-composition disclosure (G6).
3. **Adopt formal recusal policy** in committee charter (G2).
4. **Decouple Alembic adoption** from the ORM debate; vote on Alembic-first independently (M7, A5).
5. **Require hardened proposal** before any migration commit: POC on one product's read path (M6), test-coverage gate (M2), code-survey for extraction depth (M3), explicit dual-stack ownership + rollback (M1), 5-product sequence plan (M5), reverse off-ramp criteria (M10).
6. **If "delay + teach better" is preferred**, require falsifiable metric + automatic re-vote trigger written into committee charter (A4).
7. **Independent of vote outcome**: require fluentql architecture docs, decision records, migration playbooks under author's name (A6) — reduces bus factor (T1) regardless.
