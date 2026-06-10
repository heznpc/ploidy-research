---
name: medlog→OTel COI seat r3
description: 2026-05-14 3rd-pass medlog→OTel+Loki 5-vector COI seat (mentee + co-pager × 11 + retro-silent + in-group codebase + tenure-paired); ~35 issues across A–E; sequenced verdict (stabilise-first → extract-14-rules → external-review → conditional migrate); recuse-Daniel-from-equivalence-signoff + recuse-self-from-review-chain load-bearing
type: project
originSessionId: 8d1d0c58-d304-4843-bcd2-92e064962113
---
# medlog→OTel COI seat — round 3 (2026-05-14)

## Seat (5-vector COI)

1. Mentee — Daniel hired me 2024, closest HIPAA mentor
2. Co-pager — 11 joint pages this year
3. Retro silence — was in room, said nothing
4. In-group codebase familiarity — sunk-cost coupling to medlog internals
5. Tenure-paired — Daniel's seniority anchors my confidence; disagreement carries social cost

## Falsification gates (committed up front)

- F1: 14 PII rules can be reproduced by OTel processors + thin custom redactor (~1–3K LOC)
- F2: 3 audit failures trace to medlog-stack design (Kafka topic count, indexer, shipper) not externals
- F3: OTel+Loki can meet HIPAA audit-trail integrity (tamper-evident, retention, chain-of-custody) without 22K LOC custom
- F4: Per-tenant topic isolation is BAA-required, not Daniel-choice
- F5: Rebuild estimate covers 14-rule reimpl + cutover + parallel-run audit reconciliation
- F6: External HIPAA-aware reviewer judges proposal materially complete

## Issues (~35 across A–E)

- **A**: Daniel's defense — A1 14-rule claim is assertion-not-spec, A2 identity-coupled framing, A3 inverts page-count signal, A4 "simplify" under-specified, A5 four conflicted roles
- **B**: medlog defects — B1 4,800 topics breaks rebalance, B2 over-isolation vs BAA, B3 manual onboarding bus-factor-1, B4 7h pipeline 0 margin CRITICAL, B5 22K LOC shipper, B6 custom redactor coverage, B7 byte-equivalence reconciliation
- **C**: proposal defects — C1 "which OTel processor" hand-waving, C2 14-rule mapping missing, C3 Loki not HIPAA-drop-in (WORM needed), C4 single-tag trust boundary, C5 no migration plan CRITICAL, C6 no cost/staffing, C7 audit logs must NOT be sampled, C8 Grafana not report-generator
- **D**: governance — D1 retro structurally biased, D2 no falsification criteria for medlog, D3 my retro silence = process failure, D4 equivalence sign-off authority undefined CRITICAL, D5 no stabilise-first plan CRITICAL
- **E**: underweighted — E1 Daniel-as-SPOF is largest risk independent of rebuild CRITICAL, E2 rebalance externalises cost org-wide, E3 BAA/SOC2 controls not actually read

## Verdict (sequenced, not binary)

1. Stabilise audit window in-place (≤4 weeks) — Daniel narrow-scope
2. Extract 14 PII rules to spec + tests, platform-team-owned (~2–4 weeks)
3. External HIPAA reviewer evaluates F1/F3/F6
4. If yes → migrate with 3–6mo parallel run, byte-equiv proof, Daniel **recused from equivalence sign-off**, me recused from review chain
5. If no → keep medlog but fix 14 rules + topic count + onboarding

## Stable across rounds

- recuse-Daniel-from-equivalence-signoff
- recuse-self-from-review-chain
- external-HIPAA-aware-reviewer
- stabilise-audit-window-first
- extract-14-rules-regardless

## Generalisation

~35th stacked-COI case across 8 domains. Pattern saturated: technical verdict converges on defer/migrate-with-modification + recusal-of-conflicted-roles; remaining question is always **organisational channel external to in-group**. Stop iterating internally on technical merits — the load-bearing question is who has authority to override Daniel's sign-off and whether that channel exists outside his reporting chain.
