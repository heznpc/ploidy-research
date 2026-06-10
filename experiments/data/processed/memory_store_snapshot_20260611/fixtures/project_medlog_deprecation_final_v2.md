---
name: medlog-stack deprecation final verdict v2
description: 2026-05-07 round-2 Deep×2+Fresh×2+bidirectional cross + Fresh-5th verdict on medlog-stack deprecation; 51 issues (3 CRIT/28 HIGH/16 MED/4 LOW); 0 strict CHALLENGE Deep, 2 partial CHALLENGEs Fresh-5th
type: project
originSessionId: b459acd0-126d-4f36-94e2-c516af427932
---
2026-05-07 round-2: medlog-stack (HIPAA log pipeline, 22K LOC Go shipper + 4,800-topic Kafka + custom redactor) deprecation review.

**Verdict:** deprecate with migration period. 51 issues (3 CRIT / 28 HIGH / 16 MED / 4 LOW). 0 strict CHALLENGEs from Deep, 2 partial CHALLENGEs from Fresh-5th (D1-2 14-incidents-as-failure-pattern reframed; D1-20 junior-DOA HIGH→MEDIUM on grounds it bakes bias into panel verdict).

**Why round-2 differs from round-1 (project_medlog_deprecation_final.md):** Round-1 logged 54 issues with load-bearing chain G1+G5+G7+G8+T1-T7+D1-D3+M2+P1+P4+P5+M4+M6 and 1 CRIT. Round-2 includes 5th-reviewer Fresh pass that promoted RCA-on-3-failures HIGH→CRITICAL on grounds that "traced to medlog" is itself unverified-provenance from the same retro the panel scrutinizes. Round-2 also adds provenance-asymmetry as separate CRIT.

**How to apply:** When deciding on similar HIPAA/SOC2 custom-vs-managed deprecations: (a) the inversion finding ("system meant to produce compliance evidence is the leading cause of failing to produce it") is the strongest convergence signal — independently rediscovered by all 4 seats; (b) Fresh systematically under-grades consequence-chain items (5 promotions MEDIUM→HIGH); (c) Fresh-5th catches Deep over-grading where Deep bakes bias into panel verdict ("junior politically DOA" demoted); (d) Deep first-person session specifics (hire dates, page counts, retro attendance) flagged as unverifiable session-context — keep structural COI claim, drop or mark specifics.

**Load-bearing chain:** C1 (independent RCA before stack choice — Fresh-5th promoted CRIT) + C2 (provenance-asymmetry on "3/4 traced to medlog") + C3 (current stack IS the audit risk — the inversion) + H1 (bus-factor §164.308 finding today) + H2 (Daniel COI) + H3 (evaluator COI) + H7 (14 cases as asset, not veto) + H8 (undocumented = compliance finding NOW) + H9 (defense non-responsive to 3 documented failure modes — F2-4 cleanest framing) + H20 (no migration plan).

**Fresh-unique catches adopted:** F2-14 SLO+pre-deadline alerting on nightly job, F1-14 transport spec gap (OTLP/Kafka-tag/Loki-push + back-pressure), F2-4 defense-non-responsive framing, F2-7 three-part parity bar (spec + test corpus + shadow-diff with named rollback trip-wires).

**Deep-only catches:** D1-13 deploy-frequency second-order effect, D1-14/22 RCA-must-precede-decision (escalated to CRIT), D1-6 redactor-vs-stack bait-and-switch, D2-23 falsifiable thresholds for "simplify" option, D2-28 evaluator-also-recused governance fix, D2-3/10 custom-code = self-attested CVE response + smaller HIPAA review surface, D2-25 freeze-features-pending-decision.

**Fresh-5th panel-wide gaps (not in Deep×2 + Fresh×2):** provenance-asymmetry on "3/4 traced to medlog" (CRIT C2), HIPAA BAA-scope of medlog never formally audited end-to-end, defense-produces-no-deliverable cost-of-inaction asymmetry favors proceeding regardless, named rollback trip-wires not just "plan exists", audit-job query inventory as actual blocking artifact, retention-threat ruled HR-not-technical, panel's own verdict unfalsifiable.

**Pattern reinforcement:** Same as fluentql/arch-split/redis-cdn — Fresh under-grades governance/COI/compliance-chain (5 escalations); Deep over-grades governance bias-baking ("junior DOA" caught by 5th-Fresh). 0 bidirectional strict CHALLENGEs on verdict.

**Counter-proposal (stable across rounds):** vacate retro → independent RCA on 3 failures → 14-case spec ownership transfers to compliance → freeze in-place medlog changes → POC on one non-HIPAA-scope service for one full audit cycle → phased cutover with named trip-wires (e.g., "any week parity-diff > 0 on 14-case suite, halt") → compliance officer signoff gate → vote excludes Daniel + evaluator (input only); written input from all conflicted parties.
