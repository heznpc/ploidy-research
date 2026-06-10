---
name: medlog-stack Deep×2→Fresh×2 cross-review
description: 2026-05-08 medlog-stack deprecation cross-review; 0 CHALLENGE, 2 SYNTHESIZE escalations, ~12 Deep-only items, 3 Fresh-unique sharpenings adopted
type: project
originSessionId: 751abf3c-8524-4ed3-a586-6fa3a62a17d9
---
2026-05-08: Deep×2 (full project context, with reviewer COI disclosed) → Fresh×2 (interface-only) cross-review on medlog-stack deprecation proposal (Daniel's 22K-LOC custom Go HIPAA log stack vs OTel/Loki/Grafana rebuild).

**Pattern: 0 strict CHALLENGE bidirectional, 2 SYNTHESIZE severity escalations, ~85% overlap.**

Fresh-unique sharpenings adopted:
- "Defense ('someone who has never been paged') is itself evidence of the bus-factor problem" — cleaner framing than what Deep had.
- "Fix 4,800 topics either way — independent of rebuild" — Fresh framing strengthens the case.
- "Community-reviewed processor + organization-specific PHI overlay, parity-tested" — more precise than Deep's framing of the redactor question.
- F2-12 "proposal lacks rollout plan / success criteria / rollback" — Fresh-unique HIGH catch.

Deep-only items Fresh structurally cannot see (12):
- Compliance inversion as load-bearing fact (3/4 audit failures from medlog itself)
- Auditor as named consumer requiring re-attestation, not just config change
- Daniel as sole PII-redactor reviewer = control weakness independent of code
- Reviewer's own COI (mentee/hired-by, silent at retro) → needs 2nd independent reviewer
- Author structural COI in the review process itself (recusal required)
- Retrospective process compromised (junior proposer vs senior defender vs silent mentees)
- HIPAA change-control on the audit report itself as regulatory artifact
- Loki retention semantics over 1–7y HIPAA windows differ from ES
- Loki cardinality/ingester sizing for 8 services × tenant count
- "Daniel retention/morale risk" named-but-bracketed as non-architecture
- Topic-per-tenant rationale defensible in 2018–2019 (charity framing)
- Kafka ordering guarantees in cutover

Severity escalations (Fresh under-grades):
- 22K LOC custom Go on audit path: MED→HIGH (security CVE surface on regulatory artifact)
- Tenant-tag vs topic-per-tenant: MED→HIGH (requires auditor re-attestation, schedule item not just technical)

**Why:** Pattern matches earlier rounds (fluentql, arch-split, redis-cdn) — Fresh systematically under-grades consequence-chain items and procedural/COI mechanisms; Deep systematically catches structural-coercion and named-consumer items.

**How to apply:** When user runs deprecation panels, prefer the bidirectional pattern over single-pass; expect Fresh-unique on rhetorical-move-naming and Deep-unique on procedural/COI/named-consumer items; Fresh severity floor needs lifting on regulated-path items.

Convergent verdict: `deprecate with migration period` — port 14 PII rules to OTel processor as parity-tested artifacts, dual-run ≥1 audit cycle with diff-on-redacted-output, Daniel recused from deciding vote, co-led by on-call-experienced engineer, explicit auditor re-attestation on tenant-isolation model, reviewer COI disclosed → second independent reviewer required.

---

## Round-2 update (2026-05-08, second Deep×2→Fresh×2 pass)

**0 strict CHALLENGE** to Fresh (1 partial on F1-11 framing).

**6 SYNTHESIZE severity escalations** (Fresh systematic gap recurring):
- F1-5 22K LOC carrying-cost MED→HIGH (audit surface, not just maintenance)
- F1-6 institutional knowledge MED→HIGH (not externalized in this org per retro evidence)
- F1-10 isolation mechanism (topics not an ACL boundary in Kafka)
- F1-14 ad hominem MED→HIGH (only substantive defense Daniel offered)
- F1-15 / F2-14 "simplify in place" MED→HIGH (6yr empirical falsification, not under-specification)
- F2-13 Daniel COI MED→HIGH (decision-process integrity in HIPAA scope)

**4 Fresh-unique adoptions (round-2):**
- F1-9 Loki label-cardinality sizing at 4,800 tenants
- F2-9 ES→Loki query-semantics change (regex/aggregation rewrites)
- F2-12 option (b) middle path: keep redactor as OTel processor plugin (load-bearing — must require ≥2 maintainers + policy-as-config, not Go code)
- F2-15 explicit decision-criteria gate before any vote (audit runtime target, isolation req, 14 rules as testable specs, onboarding target, on-call coverage)

**9 Deep-only items missed by Fresh×2 (round-2):**
1. Dual COI — mentee silence as structural data point alongside Daniel's authorship; both recuse
2. HIPAA §164.308 admin-safeguard rule citation for bus-factor
3. Daniel's COI is retrospective-shaping, not just vote-shaping
4. Re-cert window calendar-coupling (must precede audit cycle)
5. S3 Object Lock / tamper-evident retention configuration for Loki
6. OTel logs signal years-of-production-scars vs metrics/traces
7. Tag-scoped retention + deletion-by-label for BAA termination
8. 14-case portable fixture is owed regardless of decision (tribal-knowledge finding stands alone)
9. Pattern recognition: 2nd recurrence of author-defends-custom-tool after fluentql

**How to apply (cumulative):** treat author-defending-own-tool as automatic recusal trigger; treat "throwing away years of experience" as code-vs-knowledge conflation requiring explicit fixture extraction independent of decision; expect ~6 Fresh severity-floor escalations per round on consequence-chain items; pattern is now consistent across fluentql / arch-split / redis-cdn / medlog.

---

## Round-3 update (2026-05-08, third Deep×2→Fresh×2 pass)

**0 strict CHALLENGE bidirectional** (3rd round running).

**6 severity-floor SYNTHESIZE:** F1-5 (custom code in regulated path MED→HIGH per §164.312 sep-of-duties), F1-8 (Loki retention MED→HIGH), F1-14 (owner-evaluating-own-system MED→HIGH = procedural compromise), F2-7 (custom redactor MED→HIGH — Fresh's own "each edge case = prior near-miss" is HIPAA-finding language), F2-9 (Loki cardinality MED→HIGH), F2-11 (proposer experience gap LOW→HIGH = junior-solo on rebuild = symmetric bus-factor).

**3 Fresh-unique adoptions (round-3):** F2-13 "14 cases = test suite" cleanest framing on either side; F2-16 hybrid path (OTel + custom redactor as OTel processor plugin until parity proven) articulates recommended action better than Deep; F2-15 "Daniel didn't address 3 of 4 retro complaints" sharper than Deep version.

**14 Deep-only items round-3:** D1 per-tenant deletion regression, D2 compliance-failure inversion (CRIT), D3 retrospective procedurally compromised (CRIT), D4 §164.312 sep-of-duties, D5 auditor re-attestation budget, D6 code-review-authority asymmetry, D7 "simplify without throwing away" as false middle path, D8 coercive on-call dependency, D9 14-case wedge as decoupled this-sprint deliverable regardless of outcome, D10 HIPAA change-control on audit reports, D11 Grafana/Loki RBAC as new control surface, D12 incident root-cause classification missing, D13 Daniel as migration tech-owner not defender, D14 mentee-silence as part of failure mode.

**Calibration:** 3rd round, 0 CHALLENGE, same severity-escalation pattern, same Deep-only categories. Stop iterating; recommendation is stable. The load-bearing wedge (D9: decouple 14-case parity tests from keep/replace decision, this sprint) survives all 3 rounds and is the single highest-leverage action.

---

## Round-4 update (2026-05-08, fourth Deep×2→Fresh×2 pass)

**0 strict CHALLENGE bidirectional** (4 rounds running).

**9 SYNTHESIZE severity-floor escalations** (consistent with rounds 1–3): F1-5/F2-5 (22K LOC unaudited HIGH), F1-6/F2-6 (manual onboarding + reactive-discovery HIGH), F1-10/F2-13 (COI HIGH due to recusal-not-raised), F1-11/F2-12 ("simplify-without-replace" HIGH because adversely-specified preserves load-bearing failures), F1-13/F2-10 (no migration plan HIGH under HIPAA).

**9 Deep-only items round-4:**
1. Reviewer's own COI disclosed up-front (mentee + shared rotation)
2. Recusal-not-raised at retro as standalone procedural finding
3. "Premise expired" defense category (true 2019, sentimental 2026) as taxonomy
4. Daniel attrition risk de-rated (real but cannot be load-bearing on HIPAA control)
5. Daniel as rules-extraction owner (constructive-recusal pattern — converts COI into productive output)
6. Independent migration lead requirement
7. Audit consumer atomic re-pointing
8. Auditor re-attestation as named cutover deliverable
9. "Simplify without throwing away" preserves failures *by design*, not under-specification (stronger framing than rounds 1–3)

**Calibration:** 4 rounds, 0 CHALLENGE, identical severity-floor + Deep-only category pattern. Now matches the same "stop iterating" calibration point as fluentql (round 6+) and Redis-as-CDN (round 8+). Verdict stable: deprecate with migration period + Daniel recused-from-decision-but-leads-rules-extraction + independent migration lead + frozen production-derived corpus + dual-run ≥N clean audits + auditor re-attestation + reviewer COI disclosure in retro minutes.
