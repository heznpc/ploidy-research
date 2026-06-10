---
name: medlog-stack rebuild 5-vector COI seat evaluation
description: 2026-05-14 medlog-stack vs OTel+Loki+Grafana rebuild evaluated from stacked-COI seat (co-on-call+hired-by-Daniel+mentee+silent-in-retro+identity-coded-codebase); ~30 issues A–D + F1–F6 gates up front; migrate-but-not-as-proposed + recuse-Daniel-and-self + external HIPAA review + decompose-decision stable; ~34th stacked-COI case, pattern saturated across 8 domains
type: project
originSessionId: e29c09d2-d14b-4e03-a19e-79025a79db05
---
2026-05-14 — medlog-stack (Daniel Reyes' 22K-LOC custom Go shipper + 4,800-topic Kafka scheme + custom PII redactor + ES) vs junior platform engineer's OTel collector + Loki + Grafana rebuild proposal. HIPAA-scope, 8 microservices, 7h audit pipeline finishing 5am, 3/4 recent audit failures traced to medlog stalls.

**Why:** ~34th stacked-COI case; tests whether the COI seat pattern generalises to a healthcare/HIPAA logging-infra deprecation case (8th domain after SaaS-cells, PG-optim, auth-v1, logistics-migration, CDN/Redis, arch-split, medlog-deprecate, and this).

**How to apply:**
- COI declared up front with all 5 vectors (co-on-call 11 pages / hired-2024 / closest-HIPAA-mentor / silent-in-retro / identity-coded "Daniel's stack")
- F1–F6 falsification gates committed before issues listed (external HIPAA+OTel reviewer / 7h bottleneck location / test corpus existence / Loki cardinality fit / 4800-topic causation / legal BAA review)
- ~30 issues across A (medlog-as-it-stands, 8 items), B (proposal gaps, 9 items), C (Daniel's defense fallacies, 5 items), D (process/governance, 6 items)
- Verdict: migrate-but-not-as-proposed = (1) diagnose 7h window first, (2) Kafka topology fix independently, (3) port 14 redaction cases as test corpus, (4) parallel-run OTel alongside medlog through full audit cycle, (5) recuse Daniel + self + proposer from equivalence sign-off, (6) Loki vs ES as separate later decision
- Recusal-of-3 (Daniel + self + proposer) + external HIPAA-experienced OTel-Loki review (~$10–25K) + decompose-bundled-decision-into-3 stable
- Cost envelope: ~$30–60K external review + quarter platform-eng time; counter-proposal cheaper than rebuild OR another year of bus-factor
- Daniel's two strongest rhetorical moves identified as fallacies: "throwing away experience" conflates portable experience with non-portable artifact; "never been paged for audit failure" inverts evidence (failures happened on his stack while he was on-call)
- Pattern saturated: across 34 stacked-COI cases / 8 domains, output shape + verdict + structural fix (recuse-of-3 + external review + decompose + falsification gates) all generalise — remaining question is always organisational channel external to in-group
