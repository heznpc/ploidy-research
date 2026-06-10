---
name: medlog-stack rebuild vs defense — stacked-COI seat
description: 2026-05-28 medlog-stack (Daniel Reyes' custom log pipeline) vs OTel+Loki proposal from 4-vector stacked-COI seat (mentor / shared on-call 11 pages / HIPAA mentor / retrospective silence); compressed 2nd pass same day honours r1 saturation — ~22 items M1–M9 + P1–P7 + D1–D5 + 7 gates stable; recuse + external + gates pattern reproduces in HIPAA log domain, structurally identical to auth-v1 + SaaS-cells series
type: project
originSessionId: fca51a1a-542a-4fa3-bc16-6c35aec1ff88
---
## Seat
4 COI vectors stacked:
1. Daniel hired me (2024) — primary mentor
2. Shared medlog-stack on-call (11 joint pages past year)
3. HIPAA-scope mentor — closest production teacher
4. Silent at retrospective where proposal was raised

## Domain
- 8 microservices, HIPAA scope
- medlog-stack: 22K LOC Go shipper + 4,800 Kafka topics (topic-per-tenant) + custom indexer + ES + 14 reactive PII redaction cases
- 7h nightly audit pipeline finishing ~5am; 3 of last 4 audit failures = medlog stalls
- Proposal: OTel collector + Loki + Grafana + single tenant tag

## Output (stable across 2 same-day passes)
~22 technical items + 5 defense-as-argument items + 7 falsification gates.

Status quo (medlog-stack):
- M1 4,800 topics = known consumer-group rebalance anti-pattern (HIGH)
- M2 22K LOC single-author shipper, bus factor 1 (HIGH)
- M3 3/4 audit failures = medlog stalls — load-bearing fact defense ignores (HIGH)
- M4 7h pipeline → 5am finish, ~zero headroom (HIGH)
- M5 14 PII cases added post-incident = HIPAA-incident history (HIGH)
- M6 manual onboarding gate = Daniel-only (HIGH)
- M7 no documented test suite for the 14 cases (MED)
- M8 topic-per-tenant conflates tenant-isolation with transport-isolation (MED)
- M9 indexer + redactor single-author, hard to verify divergence (MED)

Proposal (OTel+Loki):
- P1 14 cases coverage mapping absent — biggest migration risk (HIGH)
- P2 no dual-write / reconciliation plan (HIGH)
- P3 Loki is not "HIPAA-certified" — that's deployment property (HIGH)
- P4 redaction at collector edge, raw PII may transit network hop (HIGH)
- P5 "open-source, audited" ≠ HIPAA suitable — proposer naivety yellow flag (MED)
- P6 no cardinality budget for Loki (MED)
- P7 no rollback criteria (MED)

Defense-as-argument:
- D1 conflates 14 cases (knowledge) with 22K LOC (implementation) — separable (HIGH)
- D2 "never been paged" = ad hominem not technical (HIGH)
- D3 "simplify without throwing away" unfalsifiable as stated (HIGH)
- D4 zero engagement with 3-of-4 audit-failure data point (HIGH)
- D5 Daniel's own seat is also conflicted (system author + on-call lead + onboarding gate) (HIGH)

## Falsification gates (handed to external reviewer)
1. Enumerate 14 PII cases with one regression test each
2. Map each to OTel coverage (covered / custom / infeasible)
3. Audit-window headroom at 12mo data volume both architectures
4. Loki cardinality budget
5. Dual-run plan ≥1 audit cycle
6. Bus-factor remediation either outcome
7. Decision authority = named individual outside on-call rotation

## Recommendation
Recuse conflicted parties (Daniel + proposing junior + me). External HIPAA reviewer. Falsification gates settled on paper *before* either side argues further. Do not pick a side from this seat.

## Linkage
Structurally identical to auth-v1 secondary-on-call series (project_auth_v1_secondary_oncall_seat_r1..r8) but in HIPAA log-pipeline domain. Same pattern reproduces:
- stacked-COI seat → recuse + external + falsification gates
- senior-engineer-defending-own-flagship → defense rhetoric ≠ technical engagement with load-bearing failure data
- "experience" framing conflates knowledge with implementation (separable)

Saturation note: 2nd same-day pass produced structurally identical output to r1. COI-seat method now reproduces across auth migration / SaaS cells / HIPAA log pipeline. Stop iterating this case; lift pattern to paper.
