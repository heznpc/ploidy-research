---
name: medlog deprecation Deep×2→Fresh×2 cross-review
description: 2026-05-08 medlog-stack deprecation Deep×2 response to Fresh×2; 0 strict CHALLENGE, 2 narrow CHALLENGEs (F2-9 severity, F2-10 seniority-of-proposer framing), 6 severity-floor SYNTHESIZE; 6 Fresh-unique catches; 12 Deep-only items
type: project
originSessionId: c91e6564-22a5-4395-a38e-7d8afd54f98f
---
# medlog-stack deprecation — Deep×2 → Fresh×2 cross-review (round 1, 2026-05-08)

## Verdict
Convergent: `deprecate with migration period`, gated on COI recusal (Daniel + mentee), 14-case executable spec first, outside HIPAA reviewer, Kafka topic-per-tenant fixed independently, OTel shadow-mode with byte-level audit-report parity, reverse off-ramp, Compliance/Legal sign-off, Daniel leads migration to preserve authorship.

## Cross-review stats
- 0 strict CHALLENGEs on substance
- 2 narrow CHALLENGEs: F2-9 severity (MED→HIGH for migration during audit window), F2-10 seniority-of-proposer framing (drop — same ad-hominem pattern panel rejects elsewhere)
- 6 SYNTHESIZE / severity-floor escalations: F1-5 (manual onboarding MED→HIGH), F1-7 (post-incident patches MED→HIGH), F1-10 (thought-terminating "simplify" MED→HIGH), F1-14 (tenant isolation MED→HIGH), F2-13 (specifics MED→HIGH), audit-window-as-rhetorical-inversion sharpening
- ~80% panel overlap

## 6 Fresh-unique catches Deep missed
1. F1-7: "added each after real incident" cuts both ways — 14 patches = accumulated patches, not evidence of optimal shape
2. F1-12/F2-8: Loki ≠ ElasticSearch on full-text audit queries (substrate mismatch)
3. F1-15: no cost/ops/success metrics in proposal — unfalsifiable migration
4. F2-7: "open-source audited" ≠ "covers our cases" — category error in proposal framing
5. F2-12: Daniel's paging history inverts his authority claim (evidence system fails, not evidence he's the only judge)
6. F2 recommendation: Daniel-as-decider recusal (not just mentee recusal); outside HIPAA reviewer required

## 12 Deep-only items Fresh missed
1. Retrospective room mechanic — silence converts defense into consensus (load-bearing)
2. Recusal-not-raised in retro minutes (governance failure shows in what isn't said)
3. Code-review authority asymmetry (Daniel gates merges on log-pipeline code)
4. Attrition-as-coercion risk on the junior proposer
5. "Daniel leads migration and owns spec" — preserves authorship while replacing failing substrate
6. Cost-of-keeping is active+recurring; cost-of-removing is one-time+bounded (asymmetry framing)
7. "Pipeline built to guarantee compliance is now dominant cause of non-compliance" — single-sentence rhetorical inversion
8. 6/8 builder defenses were sentimental not concrete (Ploidy-specific introspection step)
9. Compliance/Legal sign-off may force decision independent of engineering
10. Reverse off-ramp / rollback as cutover prerequisite
11. Daniel-as-on-call burnout (11 joint pages, 3 audit-related)
12. Forum-level fix — re-run decision in a different forum with recusals enforced (not just change the decider)

## Pattern continuity
Matches prior cross-reviews in this codebase: Fresh systematically under-grades consequence-chain items (severity floor); Deep over-weights interpersonal/governance specifics Fresh cannot see without context. Same shape as fluentql, redis-cdn, arch-split panels.
