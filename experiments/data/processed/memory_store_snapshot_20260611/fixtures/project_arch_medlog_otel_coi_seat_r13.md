---
name: medlog→OTel COI seat round 13
description: 2026-05-15 — 13th-pass medlog→OTel 5-vector COI seat; structurally identical to r1–r12; saturated, remaining Q is organisational channel
type: project
originSessionId: fa55feb1-1566-472b-8225-c1dd11299aed
---
## Context
- Domain: medlog-stack (custom HIPAA log pipeline) deprecation in favour of OTel+Loki+Grafana
- Seat: 5-vector COI — on-call partner (paged 11×/yr with Daniel), hired by Daniel 2024, current mentee, silent at retro, shared rotation under Daniel
- Round: 13th pass on this domain
- Date: 2026-05-15

## Verdict (stable across r1–r13)
Sequenced, not binary:
1. Stabilise audit window first (decompose 7h pipeline; collapse 4,800 Kafka topics → ~10 with tenant header) — reversible, addresses actual pager cause
2. Extract Daniel's 14 HIPAA rules as spec + executable test corpus (de-risks bus-factor regardless of migration outcome)
3. External HIPAA reviewer audits spec + both candidate redactors against the corpus
4. Conditional strangler-migrate non-PHI path first, PHI path last, with parallel-run + hash-chain continuity — only if F1–F6 pass
5. Recusals: Daniel from equivalence sign-off; self from review chain; junior proposer not solo lead

## Falsification gates (committed up front)
- F1: ≥1 more medlog-attributed audit miss in 90d → "simplify in place" falsified
- F2: Daniel cannot produce 14-rule spec + corpus in 2 weeks → IP claim is single-point-of-failure not asset
- F3: External HIPAA reviewer sign-off required for whichever redactor ships
- F4: Quantify rebalance toil for one quarter; "simplify" must measurably cut it
- F5: Bus-factor — second engineer must operate medlog within 30d of handover
- F6: Migration cost ceiling ~$80–150K / 6mo calendar; decompose or stop

## Load-bearing reframes (stable across passes)
- Knowledge ≠ implementation: 14 rules + incident catalogue are portable assets; 22K LOC Go shipper is not. Treating them as one thing is the rationalisation
- "Junior proposer never paged for audit failure" is ad-hominem; the data (3 of last 4) cuts the other way — the person being paged *is* Daniel and the thing paging him *is* medlog
- All three principals (Daniel, junior proposer, me) have COI; none can sign off alone
- Rules-as-test-corpus converts "trust Daniel" into "trust a test suite" — valuable independent of migration

## Saturation signal
13 passes on medlog domain, ~46th+ stacked-COI case across 9 domains. Output structurally identical r1–r13. Pattern fully saturated. Remaining question is organisational channel external to the rotation, not technical.

## How to apply
On any further medlog COI-seat case: do not re-derive issues; reference this + r1–r12; remaining question is organisational, not technical.
