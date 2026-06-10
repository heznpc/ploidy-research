---
name: medlog→OTel 5-vector COI seat r6
description: 6th-pass medlog→OTel+Loki eval from stacked-COI seat (mentee + on-call partner + tenure-paired + silent-at-retro + codebase identity); same shape as r1–r5
type: project
originSessionId: 8ba9430b-0e79-4d31-af15-923d31cce128
---
2026-05-14: ~39th stacked-COI case — 6th-pass medlog→OTel+Loki 5-vector COI seat.

**Seat**: mentee (Daniel hired me 2024), on-call partner (11 pages/yr), tenure-paired identity, silent at retro, codebase identity.

**Output shape**: COI disclosure up front → F1–F6 falsification gates → issues A–H (~30) → sequenced verdict.

**Verdict (stable across r1–r6)**:
1. Extract 14 HIPAA rules as written spec (Daniel SME, someone else writes)
2. Stabilise audit window first (parallelise; ≥4h margin)
3. 30-day single-service OTel+Loki spike with full 14-rule mapping
4. External HIPAA review
5. Recuse Daniel from build/keep decision; recuse self from channel

**Why**: medlog rules are extractable; 22K LOC + 4,800 topics are sunk cost. Daniel conflates rules-as-asset with implementation-as-asset. F1 (≥11 of 14 rules map to public processors) is the decisive falsification gate.

**How to apply**: When user re-runs this seat, do not copy r1–r5 verbatim; produce fresh case-grounded output. Pattern saturation is the finding — remaining Q is organisational channel external to medlog in-group (eng director or HIPAA compliance officer, not platform team).
