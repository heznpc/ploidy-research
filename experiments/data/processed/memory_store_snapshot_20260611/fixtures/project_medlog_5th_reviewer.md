---
name: medlog deprecation 5th-reviewer Fresh pass
description: 5th-reviewer Fresh cross-review of Deep×2+Fresh×2 panel on medlog-stack deprecation; convergence on "deprecate + phase + recuse + parity-gate" but anchored numbers unverified
type: project
originSessionId: 24c5d20f-77c9-4123-98fb-a590f2555c48
---
2026-05-07: Cross-reviewed medlog-stack (custom Go shipper + 4,800-topic Kafka + custom ES indexer + custom PII redactor) deprecation panel as 5th-reviewer Fresh.

**Panel verdict (Deep×2 + Fresh×2):** deprecate medlog, phase migration (shipper → topics → redactor last), recuse Daniel from decision but keep him as migration tech lead, gate cutover on golden-corpus parity test of 14 PHI rules + HIPAA re-attestation.

**5th-Fresh additions:**
- 5 strict CHALLENGEs: F1#11 ad hominem framing too soft; F2#7 "MEDIUM confidence overstated" is unfounded pre-judgment from a Fresh seat; F2#16 effort estimate severity LOW/MED → HIGH; "~1k topics" and "4,800 anti-pattern" are anchored numbers without partition/broker calibration; D2#8 "cosmetic isolation" should be conditional on ACLs.
- 10 panel-wide gaps:
  - G1 anchored-number provenance (22K LOC, 4,800 topics, 14 cases, 3/4 audit failures, 7h pipeline, 11× paged) — none verified, all repeated as fact
  - G2 auditor not consulted as Phase-0 — re-attestation/dual-run/WORM/tag-isolation are auditor's call
  - G3 three-option framing collapsed: full-replace vs keep-medlog-as-thin-orchestrator vs status-quo never put on same ledger
  - G4 managed alternatives (Datadog, Splunk Cloud, AWS CloudWatch+Macie) ignored vs self-hosted Loki/Grafana
  - G5 Loki AGPL3 licensing graded LOW — in audit-pipeline context with any SaaS surface, MED-HIGH
  - G6 golden-corpus source is itself a regulated artifact (real PHI samples have access controls)
  - G7 attrition risk during the decision itself — recusal+public-deprecation often produces keyholder exit mid-migration
  - G8 Loki audit-query validation should be Phase-0 prerequisite gate, not "we'll find out in phase 3"
  - G9 format of original proposal unknown (RFC vs Slack vs retro one-liner) — affects fairness of "proposal lacks X" critique
  - G10 post-migration on-call rotation unplanned — Daniel is on-call because he's the only one who knows the stack
- Severity recalibration: trust-boundary change MED→HIGH; effort estimate LOW/MED→HIGH

**Why:** Establish that even after Deep+Fresh×2 panel, a 5th Fresh pass surfaces verifiability gaps (anchored numbers, missing auditor conversation, missing managed-option compare). Pattern matches prior cross-reviews: Fresh seats repeatedly under-grade consequence-chain items (compliance, retention, attrition).

**How to apply:** For HIPAA/regulated deprecation reviews, treat anchored numbers in the brief as unverified by default; require auditor consultation as Phase-0; force managed-vs-self-hosted comparison on same ledger; flag golden-corpus construction as itself a regulated activity.

---

## v2 5th-Fresh pass (2026-05-07, second sitting on same panel)

5 CHALLENGEs:
- D2-11 "tribal knowledge lost on departure" doubles as anti-recusal rationale; clean form = test corpus is the forcing-function, not Daniel running migration.
- OTel+Loki+Grafana as named replacement undefended in Deep×2, inherited by Fresh×2; "deprecate medlog" must be decoupled from "build this specific stack."
- Bus-factor remedy fix only works if rebuild itself isn't bus-factor-1 on Daniel or on lone proposer.
- F2-15 LOW/MEDIUM on junior solo-leading HIPAA migration — should be HIGH; pairing is precondition.
- Fresh sessions soften D2-18 hard verification gate into "next step is parity analysis"; should remain blocking precondition.

8 panel-wide gaps (overlap with v1: G2=#7, G4=#2-partial; novel in v2):
- Tamper-evidence (append-only/signed/hashed chains, S3 Object Lock) absent both stacks — HIGH blocking
- Cost model absent both sides (medlog carrying cost vs OTel/Loki vs managed per-GB)
- Audit-consumer contract undefined (query language, fields, retention SLA, external auditor export shape)
- Governance fix for COI is procedural — needs written ADR protocol, vote excludes author + reports
- No off-ramp on migration side — D1-13 demands exit criteria from Daniel only
- Retro = actual artifact under review; none of 4 sessions return to retro to ask if proposal is best-shaped response
- "Knowledge transfers as test cases" assumed but unverified — if 14 incidents only in Daniel's head, extraction is multi-month research project not a precondition

**v1+v2 union:** Both passes converge on auditor-Phase-0, managed-comparison, anchored-number skepticism, on-call rotation planning, golden-corpus regulated-activity. v2 adds tamper-evidence, cost model, audit-consumer contract, governance ADR, migration off-ramp, retro-as-artifact, knowledge-extraction-as-research.
