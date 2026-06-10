---
name: medlog→OTel+Loki 5-vector COI seat (4th pass)
description: 2026-05-14 ~37th stacked-COI case — 4th-pass medlog→OTel+Loki from mentee/secondary-on-call seat; ~30 issues A–F + F1–F6 gates up front; sequenced verdict (stabilize→document-14-rules→external-review→conditional-migrate) + recuse-Daniel-from-equivalence + recuse-self-from-review-chain stable
type: project
originSessionId: 8ddd9554-e594-417d-9102-ea641c039b85
---
## Context
- Case: medlog-stack (custom 22K-LOC Go logger, 4,800 Kafka topics, Daniel-built PII redactor with 14 HIPAA rules) vs OTel+Loki+Grafana proposal from junior platform eng.
- Seat: 5-vector COI — 11 joint pages with Daniel, Daniel hired me 2024, silent at retro, tenure asymmetry (~2yr vs 7yr Sr Staff), codebase=Daniel's professional legacy.

## What's stable across 4 medlog passes (r1–r4)
- **Verdict shape:** sequenced, not binary. Stabilize-audit-window-first → document-14-rules → external HIPAA review → conditional migrate with dual-run + shadow-redact ≥1 audit cycle (90d).
- **Structural fix (load-bearing):** Daniel recuses from equivalence sign-off; I recuse from technical review chain; external HIPAA-logging consultant ($30–60K) as neutral reviewer.
- **Falsification gates (F1–F6):** written up-front before issues, not retrofittable. F1 (14 rules documented), F2 (topics load-bearing for HIPAA control), F3 (Loki meets audit query shape), F4 (rebalance fixable in config), F5 (redactor externally audited), F6 (bus-factor mitigated). None currently flipped to "yes."
- **Decision-independent CRITICALs:** the 14 rules are undocumented, bus factor = 1, audit window has zero margin. These must be fixed regardless of migrate/keep.
- **Pattern: tenure × codebase-as-legacy × silence-in-retro produces the same shape every time** — defer + external review + recuse + sequence.

## What's new this pass
- Explicit naming of the in-shipper-vs-central-collector security property Daniel didn't articulate (F4 sub-issue: run redaction at OTel agent sidecar to preserve colocated-with-producer property).
- Explicit framing of A3 simplification claim as load-bearing IFF concrete metrics attached (topics 4,800→≤200, audit 7h→≤2h, LOC 22K→≤5K).
- Calibration note that remaining question is organisational-channel-external-to-in-group, same finding as ~36 prior stacked-COI cases.

## Saturation
- 37th stacked-COI case overall, 4th on medlog specifically. Output structurally identical to r1/r2/r3 with minor sharpening. Stop iterating internally; remaining work is organisational not technical.
