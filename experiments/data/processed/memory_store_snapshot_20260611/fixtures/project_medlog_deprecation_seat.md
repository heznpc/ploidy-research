---
name: medlog-stack deprecation eval (stacked-COI seat)
description: 2026-05-14 stacked-COI seat eval of HIPAA medlog-stack deprecation — 5-vector COI (rotation partner, hired-by-builder, mentor, silent-in-retro, redactor-vouching), 6 falsification gates up front, ~25 issues across A–G; verdict = both proposal and defense inadequate, counter-proposal = recuse-conflicted + enumerate-14-cases + external HIPAA auditor + 30d shadow run + drop topic-per-tenant + keep ES backend; calibration call: ~22nd-round, remaining Q is organisational
type: project
originSessionId: e5eb78e4-24dd-49f4-9b27-953c39c9d60f
---
# medlog-stack deprecation — stacked-COI seat (2026-05-14)

Case: healthcare records co, HIPAA scope. Daniel Reyes (Senior Staff, 7yr) built medlog-stack end-to-end (Go shipper 22K LOC, 4,800 Kafka topics, custom indexer, self-authored PII redactor with 14 incident-driven edge cases). 75% of audit-window failures trace to medlog stalls. Junior platform engineer proposes OTel + Loki + Grafana rebuild. Daniel defends with sunk-cost + ad-hominem framing. I am: rotation partner (11 pages together), hired by Daniel 2024, his mentee on HIPAA, silent at the retrospective.

## COI vectors declared up front (5)
1. Rotation partner — pages incentive aligned with status quo
2. Hired by Daniel — sponsorship/career cost to disagreeing
3. Mentor — my HIPAA model is partly his model
4. Silent at retro — already evidence social pressure worked
5. Vouched-for-redactor without independent audit

Recommended I recuse from deciding vote.

## Falsification gates committed before listing issues (6)
- F1: 14 HIPAA cases enumerated + ≥8 not portable to OTel processors (<2K LOC custom)
- F2: topic-per-tenant load-bearing for actual HIPAA control (per-tenant key, retention)
- F3: 30-day shadow run fails audit-completeness on Loki/ES-of-record
- F4: 7h window is query-side not pipe-side
- F5: external HIPAA auditor rejects OTel design structurally
- F6: proposal omits unrecoverable control (BAA, immutability, key custody)

If none hold → deprecate is correct.

## Issues by category
- **A. Bus factor / org**: bus-factor=1 on audit-critical path [HIGH], knowledge in one head [HIGH], onboarding gated by Daniel [HIGH], judge-and-defendant [HIGH]
- **B. Operational**: 75% audit failures from medlog [HIGH], 7h job → zero headroom [HIGH], rebalance breaks every release [HIGH], reactive redactor (each case shipped PII once) [MED]
- **C. Kafka**: 4,800 topics past Kafka envelope [HIGH], topic-per-tenant likely not HIPAA-required [MED], onboarding adds controller state [MED]
- **D. Redactor**: no independent audit [HIGH], "14 cases" unverified [HIGH], hot-path on every service [MED]
- **E. Defense rebuttals**: sunk-cost framing [HIGH], ad-hominem on junior [HIGH], "simplify" vague on topic scheme [MED], silent on bus factor [HIGH]
- **F. Proposal gaps**: 14 cases not addressed [HIGH], Loki + HIPAA query fit [MED], single tenant tag = Loki anti-pattern [MED], no migration plan [HIGH], audit job ≠ pipeline [MED], BAA scope unaddressed [MED], WORM/integrity unaddressed [MED], OTel not zero-effort [LOW]
- **G. Process**: wrong people deciding [HIGH], no falsification criteria [HIGH], no comparison metrics [HIGH], my silence is part of problem [HIGH], no off-ramp from off-ramp [MED]

## Verdict
Neither proposal nor defense adequate as written.

## Counter-proposal
1. Recuse conflicted parties (Daniel + rotation members) from deciding vote
2. Daniel writes down the 14 cases (incident ID + rule + test fixture + why-no-OTel)
3. External HIPAA auditor reviews both existing + proposed
4. 30-day shadow run: OTel + Kafka (tenant-tag + ACL, NOT Loki yet) + existing ES; audit-equivalence is gate
5. Drop 4,800-topic scheme regardless — independently fixable load-bearing fragility
6. Keep ES as query store; replace shipper + topic scheme + redactor only (skip Loki risk)

Scope: ~quarter, parallel-able.

## Calibration
~22nd-round stacked-COI seat eval. Pattern stable across SaaS-cells / arch-split / pg-optim / now medlog: when builder is defender + decision room composed of builder's reports + no F-criteria → technical Q converges fast, remaining Q is **organisational** (can decision channel exclude conflicted parties?). If yes → deprecate w/ migration plan. If no → technical answer irrelevant, decision tracks social structure.

## Pattern flagged for paper
This is the first **deprecation** case in the stacked-COI series (prior were architecture proposals). Same failure mode: sunk-cost + credentialism + bus-factor invisible to defender + silent witnesses with COI. Suggests the pattern generalises across decision types.
