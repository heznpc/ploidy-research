---
name: medlog→OTel 5-vector COI seat r11
description: 2026-05-14 — 11th-pass medlog→OTel 5-vector COI seat (~44th stacked-COI case); ~30 issues A–H + F1–F6 gates up front; sequenced stabilise→extract-14→external-HIPAA→PoC→conditional migrate + recuse-Daniel-and-self stable; pattern saturated
type: project
originSessionId: 9a66f7ae-415d-4d0c-bfdc-48a46d91ed82
---
11th-pass evaluation of the medlog→OTel/Loki/Grafana proposal from the mentee+co-on-call+silent-in-retro+codebase-identity+rotation-authority-gradient seat (5-vector COI).

**Seat vectors:**
1. Daniel hired me in 2024 (mentee)
2. 11 joint pages in past year (shared on-call lifeline)
3. Silent during retro discussion
4. Daily work inside medlog-stack (identity-coded codebase)
5. Daniel runs the on-call rotation I sit in (authority gradient)

**Falsification gates committed BEFORE issues:**
- F1: ≥11 of 14 HIPAA edge cases map to public OTel processors
- F2: External HIPAA auditor approves OTel-processor PII redaction in writing
- F3: 30-day parallel run catches every PII case medlog catches
- F4: 30-day parallel run completes nightly audit aggregation in <7h
- F5: Kafka rebalance pain reproducible *without* the proposed migration (i.e. topic count is the root, not a symptom)
- F6: 14 rules documented, version-controlled, reviewable independent of Daniel within 30 days

**Issues (~30 across A–H):**
- A. Daniel's defense: 14-rules claim load-bearing+unverified, "never been paged" is authority appeal, conflates incidents-with-redactor, "simplify without throwing away" is the only constructive sentence
- B. Bus factor: 22K LOC single-author, manual onboarding, rules in code not spec, no test corpus disclosed — CRITICAL regardless of OTel
- C. Kafka 4,800 topics: anti-pattern confirmed but fixable without OTel; tenant isolation may explain it; Loki labels are not access boundaries
- D. 7h audit: no margin, Loki may be *worse* for aggregation, structured event store (ClickHouse/Postgres/S3+Athena) skipped entirely
- E. Migration: no plan, no equivalence test, OTel-PII-processor "audited" claim needs verification, no cost scoping, sequencing wrong (migrating while paging)
- F. Third option: extract-14-rules + consolidate-topics + document-onboarding + audit-budget-alert = ~6–8 weeks, recovers most benefits without rebuild
- G. Process/governance: Daniel-recused-from-equivalence, self-recused-from-final-vote, junior proposer lacks standing, retro selected for authority gradient not best answer, no ADR
- H. Self-correction: "Daniel is partly right" holds for F5+rules-as-asset, NOT for regulatory-experience appeal; right vs rhetorical parts must be separated

**Verdict (sequenced, identical to r1–r10):**
1. Stabilise audit window (2wk)
2. Extract 14 rules into reviewable spec (30d)
3. External HIPAA reviewer evaluates spec vs OTel processors
4. Fix Kafka topic count in parallel (1–2wk)
5. 30-day PoC parallel run
6. *Then* decide between simplify-medlog / hybrid / full-OTel
7. Recuse Daniel from equivalence sign-off; recuse self from final call

**Cost:** ~$30–60K engineering + ~$5–15K external review

**Calibration:** ~44th stacked-COI case overall, ~11th on medlog-OTel specifically; verdict structure identical across all 11 passes; pattern fully saturated; remaining question is organisational (*who has authority to recuse Daniel and commission external review*) not technical.

**How to apply:** When user runs another stacked-COI eval, the answer-shape is now overdetermined. Mention saturation up front and focus output on the organisational-channel question, not on re-deriving the technical issue list.
