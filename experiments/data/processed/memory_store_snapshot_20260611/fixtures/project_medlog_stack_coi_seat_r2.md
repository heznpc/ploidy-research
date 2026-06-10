---
name: medlog-stack rebuild vs defense — 4-vector stacked-COI seat (r2)
description: 2026-05-28 2nd-pass medlog-stack vs OTel+Loki proposal from 4-vector COI seat (hired-by / shared on-call / HIPAA mentor / silent at retro); 19 issues M1–M8 + P1–P7 + D1–D4 + 6 falsification gates; pattern reproduces same-day in HIPAA log domain
type: project
originSessionId: 80026fc9-52f1-4966-892a-8c951e62136d
---
2026-05-28: 2nd pass on medlog-stack vs OTel+Loki+Grafana proposal from the same
4-vector stacked-COI seat as r1 (project_medlog_stack_coi_seat.md):
- Daniel hired me (2024)
- shared medlog on-call rotation, 11 pages together
- closest HIPAA-scope mentor
- attended retrospective, stayed silent

Output structure compressed vs r1 (22 issues → 19) but same shape:
- COI disclosure up front
- Recuse + external HIPAA-scope chair + 6-month parallel-run with chain-of-custody
- 8 medlog-side issues (M1–M8): 4,800 topics inversion, 7h-no-headroom, bus-factor=1,
  shipper supply chain, redactor coverage-vs-known-fires distinction
- 7 OTel/Loki-side issues (P1–P7): edge-case parity as load-bearing question,
  tag-vs-topic isolation downgrade, Loki WORM/retention silence, cutover chain-of-custody,
  Loki long-range query unbenchmarked
- 4 process issues (D1–D4): Daniel's appeal-to-tenure vs technical rebuttal,
  internal-room-does-not-exist, "simplify without throwing away" has no scope
- 6 falsification gates: edge-case parity table, cross-tenant isolation test,
  audit window ≤4h sustained 30d, onboarding ≤1d without Daniel, patch latency ≤7d,
  HHS-counsel-signed chain-of-custody overlap

Load-bearing finding (consistent with r1): the only technical substance in
Daniel's defense is the 14 edge cases (P1). The 4,800-topic / 7h-pipeline /
manual-onboarding issues are unanswered. Conflating tenure-appeal with
technical rebuttal is itself a process risk (D1).

New-vs-r1 sharpening: D3 named "simplify without throwing away" as a counter-
proposal that *wins by default through familiarity* unless costed against
migration with the same gates. Gates must be committed before either side
resumes writing code, not after.

Pattern: artifact-in-turn + stacked-COI seat reproduces in HIPAA log domain
same day. Recuse + external + falsification-gates-before-code stable across
both passes. Stop iterating internally; remaining question is organisational
channel for engaging external HIPAA chair, not technical.
