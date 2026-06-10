---
name: medlog deprecation — 4-session synthesis
description: 2026-05-14 4-session full-context synthesis on medlog deprecation; 25 issues (5 CRIT / 11 HIGH / 5 MED / 4 process-COI); deprecate-with-migration unanimous; recuse-Daniel-from-equivalence-signoff load-bearing
type: project
originSessionId: 507415be-c4b9-41ed-9692-419fae73bd4b
---
2026-05-14 — 4 independent full-context seats reviewed medlog deprecation (22K-LOC Go shipper + 4,800-topic Kafka + custom indexer + ElasticSearch; 14 hand-written PII redaction rules; bus-factor=1 on Daniel; 3 of last 4 audit-window failures caused by medlog).

**Verdict (4/4 unanimous):** `deprecate with migration period` — replace with OTel Collector + Loki + Grafana, gated on rule extraction + parallel shadow run + Daniel-recused equivalence sign-off.

**0 sessions recommend keep-as-is. 0 substantive CHALLENGEs bidirectional.**

**Unanimous issues (4/4):** topic-per-tenant Kafka anti-pattern; bus-factor=1 as HIPAA risk; 14 rules are the only durable asset (not the wrapper); 22K-LOC Go duplicates audited OSS; tenant isolation belongs at index/field level; stacked-COI evaluator seat must recuse.

**Majority issues (3/4):** audit failures *caused by* medlog (~75%); custom indexer + ES ops on one engineer; Daniel's "never been paged" framing is ad hominem; "simplify without throwing away" has not landed in 7 years; parallel-pipeline through full HIPAA cycle as cutover gate; Daniel must not sign off "equivalent redactor"; OTel processor gap risk; frame migration as Daniel owning rule-extraction (not "replacing his work").

**Why:** First deprecation case (vs architecture) in the series; same pattern holds — convergence across 4 stacked-COI seats, remaining question is organisational not technical.

**How to apply:** When user revisits medlog: counter-proposal is stable; load-bearing items are (1) rule extraction first, (2) parallel shadow run, (3) Daniel owns extraction but not equivalence sign-off, (4) decision authority recused from on-call rotation. Falsification gates must be written down before any "keep medlog" alternative is allowed to proceed.
