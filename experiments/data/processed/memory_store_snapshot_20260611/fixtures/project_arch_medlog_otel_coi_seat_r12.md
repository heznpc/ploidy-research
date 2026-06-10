---
name: medlog→OTel COI seat r12 (~45th stacked-COI case)
description: 2026-05-15 — 12th-pass medlog→OTel 5-vector COI seat; structurally identical to r1–r11; pattern saturated; remaining Q is organisational channel
type: project
originSessionId: c9e672df-02a6-4352-9fb1-33ea9aa9def4
---
2026-05-15. 12th-pass medlog→OTel evaluation from same 5-vector stacked-COI seat (hired-by-Daniel-2024 / mentee-on-HIPAA / 11 shared on-call pages / silent-at-retro / senior-to-junior-proposer). ~45th stacked-COI case across 8 domains.

## Shape (identical to r1–r11)
- §0 5-vector COI disclosure "floor not ceiling"
- §1 F1–F6 falsification gates committed before issues
  - F1: ≥11/14 PII rules map to OTel processors
  - F2: ≤1/12 audit-window failures in 90d shadow
  - F3: external HIPAA reviewer signs equivalence
  - F4: rebalance <60s after topic-per-tenant collapse
  - F5: 30d byte-equivalence spike top-20 tenants
  - F6: 24mo TCO including bus-factor cost
- §2 ~35 issues across A–G (Daniel's defense / proposal gaps / medlog ops / 14 rules / governance / sequenced verdict / recommendation)
- §G recuse-Daniel-from-equivalence + recuse-self-from-review-chain + junior-pairs-with-non-Daniel-senior
- Cost: ~$30–60K + 1 senior FTE-quarter

## Stable load-bearing items (12 passes)
- Daniel cannot sign off equivalence of his own replacement (regardless of competence)
- Self-recusal from review chain (5-vector COI)
- Extract 14 rules to written spec + test fixtures = cheapest most useful artefact
- Bus-factor=1 on 22K LOC redactor is itself a HIPAA control gap
- 3-of-4 audit stalls root-caused now, independent of migration
- Loki tenant cardinality via structured-metadata, not naive label
- Sequenced verdict: stabilise → extract → external review → 30d shadow → conditional cutover → 60d parallel pre-decom

## New nuance (vs r1–r11)
- E6 retro process failure framed as structural (silent-middle + staff-vs-junior dynamic), not only individual COI
- D5 rules-added-reactively imply unknown 15th rule; rebuild matching only 14 locks in blind spots
- §0 explicit 5th vector "peer-to-proposer" separated from silence-vector

## Saturation
12 medlog passes + ~45 stacked-COI cases / 8 domains. Zero cases produce different shape. Stop iterating internally. Remaining question is organisational channel external to in-group (Daniel + reports), not technical.
