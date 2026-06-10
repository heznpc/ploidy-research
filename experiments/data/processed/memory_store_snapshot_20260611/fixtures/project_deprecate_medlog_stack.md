---
name: deprecate medlog-stack case (5-vector COI)
description: 2026-05-14 — medlog-stack vs OTel/Loki rebuild eval from 5-vector-COI seat (hired-by-Daniel + mentor + on-call partner + silent-at-retro + benefits-from-status-quo); ~20 issues across M/R/D/P; rebuild leans correct, decision belongs to unconflicted reviewer
type: project
originSessionId: 17f37fa4-e05f-4a18-b40f-65f3bd717dbf
---
Case: HIPAA healthcare records co, 8 microservices. medlog-stack (22K LOC Go shipper, 4,800 Kafka topics topic-per-tenant, custom redactor, 7h audit window) built by Daniel Reyes (Senior Staff, 7yr, on-call lead). Junior platform engineer proposed OTel+Loki+Grafana rebuild. Daniel defended on "14 HIPAA edge cases + years of regulatory experience".

Evaluator seat: hired by Daniel (2024), shares on-call (11 joint pages), closest HIPAA mentor, silent at the retrospective, benefits from status quo (Daniel absorbs audit pages).

**Why:** Textbook deprecation-with-author-defending case + stacked COI seat. Useful as Ploidy paper material — same shape as SaaS-cells / arch-split / Redis-CDN cases but with mentor-as-defender twist.

**How to apply:** When evaluating proposals where the author is also the evaluator and the evaluator is the dependant: declare COI up front, separate "the experience" from "the implementation" (14 edge cases ≠ 22K LOC), separate technical merit from process problems, and recuse from the deciding vote. The third-path counter-proposal (enumerate cases as test suite → spike against suite → falsification gates → unconflicted decider) is reusable.

Load-bearing technical findings:
- M1: 4,800-topic consumer-group rebalance is structural, not tunable
- M2: bus-factor=1 on HIPAA-scope pipeline
- M3: audit-failure-then-Daniel-paged loop is SPOF presented as expertise
- R1: 14 HIPAA edge cases are the legitimate kernel of defense; migration must cover them case-by-case
- D1: "throwing away experience" conflates experience with code
- D4: Daniel cannot be deciding reviewer (built it + paged for it + gates onboarding)
- P1: junior→senior-staff power asymmetry kills proposal absent structural protection

Calibration: noted at end that "balanced" framing itself reflects COI pull; technical answer leans rebuild, open question is migration plan.

**2026-05-14 re-run via `deprecate` skill (Builder + Fresh sub-agent):**
- Same artifact, fresh evaluator seat. Builder seat's attachment-check independently caught the 14-rules-vs-22K-LOC conflation *before* Fresh ran — protocol's structure forced it.
- Fresh (zero-context sub-agent) independently flagged: commodity-2026 problem, bus-factor+4800-topics = textbook reinvention, defense justifies preserving rules not plumbing. Bidirectional convergence, 0 strict CHALLENGE.
- Builder-only load-bearing additions Fresh couldn't see: 90-day shadow/dual-run with byte-diff redactor output, auditor re-certification + output-format shim, thin-custom-OTel-processor scope ("off-the-shelf covers all 14" is not literally true), Daniel-as-migration-lead framing for retention + IP transfer.
- Daniel's defense had 3 rhetorical tells: ad-hominem on proposer, "throwing away years," conflation. Self-refutation: he cites audit risk as reason to keep medlog, but 3/4 recent audit failures = medlog stalls he was paged for.
- Verdict stable across two runs: counter-proposal, deprecate plumbing, preserve 14 rules as portable rule-set + incident write-ups, Daniel as tech lead, evaluator recuses from sign-off.
- Reusable pattern for paper: deprecate-protocol-with-author-COI consistently produces (a) counter-proposal not bare defer/proceed, (b) recusal recommendation, (c) Fresh-catches-conflation + Builder-catches-migration-mechanics complementarity.

**2026-05-14 3rd run via `deprecate` skill (different framing prompt):**
- This run added explicit *up-front falsification gates* (F1–F6) committed before listing issues — same load-bearing structural move as recent SaaS-cells/arch-split rounds.
- 20-item convergence table; 0 strict cold-reader→builder CHALLENGE; 1 *builder self-CHALLENGE* on the strongest defense ("14 cases irreplaceable" is unfalsifiable until F1/F3 run). The self-CHALLENGE is the signature of sunk-cost defense surfacing under protocol pressure — paper-relevant.
- 4 builder-unique catches Fresh couldn't generate: HIPAA chain-of-custody during cutover, vendor BAA procurement timeline (Datadog/Splunk/Grafana Cloud are not free or fast), client-specific contractual PII beyond HIPAA, decision-process recusal as structural fix.
- 1 cold-reader-unique frame builder under-weighted: *every* layer has a mature 2026 replacement, not just one (defending "OTel can't do 14 cases" was layer-by-layer myopia).
- Verdict stable across 3 runs: deprecate with migration period, parallel-run audit equivalence as gate, recusal-of-2.
- Pattern confirmed for paper: COI-disclosure → falsification-gates-up-front → builder+cold-reader convergence → counter-proposal (not defer/proceed) → recusal recommendation. Reproduces across deprecate / architecture / SaaS-cells / arch-split / pg-optim / redis-cdn debate shapes.

**2026-05-14 4th run via `deprecate` skill (`debate_solo` permission denied → presented convergence directly):**
- Same case, 4-vector COI seat explicitly named in Builder position (not appended). 15-issue convergence table.
- Builder position structured the attachment-check as a 5-row table classifying each defense CONCRETE vs SENTIMENTAL with confidence; 2 CONCRETE (rules-port, OTel-processor-day-one-gap), 3 SENTIMENTAL (topic-per-tenant PHI, "throws away experience," "junior hasn't been paged"). The table form forces classification before defending.
- Fresh sub-agent (general-purpose, public-interface only) returned 4-question reply: (1) what it does, (2) yes-still-common-2026, (3) named OTel/Loki/ClickHouse/OpenSearch/managed-Kafka/off-the-shelf-DLP, (4) **No** — single sentence: "all reinventions of capabilities that mainstream observability stacks now provide with standard tenancy and redaction primitives."
- Builder-only Fresh-couldn't-see catches: rules-as-data port path (OTTL/attribute-processor), 4–8wk dual-run + PHI-corpus diff, Loki tenant-label cardinality via X-Scope-OrgID at 4,800 tenants, Daniel-as-migration-lead as social mitigation.
- Fresh-only Builder-under-weighted catch: 22K-LOC + 4,800 topics + single-author redaction = three independent commodity-reinvention signals, not one.
- 1 self-finding flagged HIGH: silence at the retrospective from a stacked-COI seat is itself a finding (issue #14). Self-recusal-or-disclose rule confirmed.
- Verdict stable across 4 runs: deprecate with migration period, builder owns the migration (resolves attachment + bus-factor + attrition simultaneously), rule-port + dual-run as cutover gate.
- New observation for paper: Builder's strongest single rationalisation pattern across all 4 runs is conflating *rules-as-data* with *implementation-as-code*. The deprecate protocol surfaces this conflation reliably; the Fresh seat does not need to name it for Builder to be forced to name it themselves under the attachment-check structure.
