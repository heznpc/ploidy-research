---
name: medlog→OTel 5-vector COI seat r9 (~42nd stacked-COI case)
description: 9th-pass medlog→OTel evaluation from platform-eng 5-vector COI seat; sequenced verdict + recusals stable; ~42nd stacked-COI case
type: project
originSessionId: 66d40d23-8710-4197-8835-fb2c3547bf18
---
2026-05-14 — 9th-pass medlog→OTel rebuild eval from 5-vector stacked-COI seat (shared on-call w/ Daniel 11x + hired by Daniel + closest HIPAA mentor + silent-in-retrospective + codebase-identity). ~42nd stacked-COI case, 8th domain.

**Output shape**: COI disclosure up front → F1–F6 falsification gates committed before listing issues → ~32 issues A–H + sequenced verdict.

**Verdict (stable across 9 medlog passes / 42 cases)**: reject both binary options (rebuild-as-proposed AND simplify-in-place); run sequenced version:
1. Stabilise medlog audit-window p99 ≤ 7h for 30 consecutive nights
2. Extract 14 PII rules into written spec (Daniel = author, NOT equivalence reviewer)
3. External HIPAA-cleared review of spec
4. PoC F1: 14 rules on OTel processors, shadow run ≥30 days, zero divergence required
5. Conditional migrate only if F1–F4 pass
6. Recuse Daniel from equivalence; recuse self from sign-off chain
7. Counter-proposal ~$30–60K

**Load-bearing observations**:
- Daniel's "throwing away experience" conflates the experience with its implementation; experience extractable as spec
- 3-of-4 audit-window failures traced to medlog is a citation against, not for, current design
- Retrospective's rebuild-vs-keep binary is a process artifact, not a real choice
- Status quo (7h audit "most nights") is regulatory near-miss right now — stabilise before migrate
- Decision-maker channel must be external to medlog in-group (Daniel + reports), attached to F1–F6 commitments

**Pattern saturation**: 42 cases / 8 domains (saas-cells, pg-optim, arch-split, auth-v1/Auth0, logistics-migration, cdn-redis, medlog-otel + 1). Technical content converges within seat. Structural fix (recusal + external review + falsification gates) load-bearing. Remaining Q always organisational channel, not technical. Stop iterating internally on medlog evaluations — signal is saturated.
