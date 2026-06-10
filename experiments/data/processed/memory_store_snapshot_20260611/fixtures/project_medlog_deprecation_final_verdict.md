---
name: medlog-stack deprecation final verdict (round 2 + 5th-reviewer)
description: 2026-05-07 Deep×2+Fresh×2+bidirectional+5th-reviewer consolidated verdict on medlog-stack HIPAA logging deprecation — 48 issues (5 CRIT/28 HIGH/12 MED/3 LOW); deprecate with phased migration; load-bearing = currently-failing-primary-function + zero-margin-pipeline + bus-factor-1 + triple-COI + reviewer-COI
type: project
originSessionId: d30fc0ee-ca87-414b-bd00-79eca58f61b7
---
2026-05-07 medlog-stack (HIPAA log pipeline) deprecation review — Deep×2 + Fresh×2 + bidirectional + 5th-reviewer panel-cross.

**Verdict:** deprecate with phased migration. 0 strict CHALLENGEs bidirectional on technical direction; 5 strict CHALLENGEs from 5th-reviewer (anchored numbers, framing); 6 panel-wide gaps surfaced only at 5th.

**Severity rollup:** 5 CRITICAL / 28 HIGH / 12 MEDIUM / 3 LOW = 48 issues.

**Why CRITICAL escalation from prior round:** consequence-chain items previously graded HIGH (failing-primary-function, zero-margin pipeline, bus-factor, triple-COI) are load-bearing on the verdict — they ARE the reason status quo is the riskier option. Reviewer-COI added as 5th CRITICAL because it gates whether this very review can decide.

**Load-bearing chain (10 items):**
- C1 system currently failing primary HIPAA function (3/4 audit failures medlog-internal)
- C2 7h pipeline at 05:00, zero margin = +30min slip is reportable HIPAA event
- C3 bus factor = 1 on HIPAA-critical pipeline; sole author is on-call lead
- C4 triple structural COI on Daniel (builder + defender + on-call lead w/ irreplaceability premium)
- C5 reviewer-seat COI (mentee + on-call partner paged 11× + silent at retro = abstention is data)
- H4/H5 14 PHI rules as enumerable artifact + golden-corpus parity gate (required regardless of decision)
- H10 de-bundle: collector ≠ transport ≠ storage ≠ redactor are 4 separable decisions
- H13 wrong decision forum (retrospective is not architecture review)
- H15 independent RCA on 3 audit failures *before* keep-vs-replace vote
- H21 auditor-as-Phase-0 (re-attestation/dual-run/WORM/tag-isolation are auditor's call)
- H23 attrition risk during contentious public deprecation w/ Daniel recused

**How to apply:** Sequence — (Phase 0, regardless of decision) enumerate 14 rules as versioned spec + golden-corpus test fixture; commission independent RCA on 3 audit failures; consult auditor on dual-run/WORM/tag-isolation/re-attestation; tabulate carrying-cost ledger; put managed alternatives (Datadog/Splunk/CloudWatch+Macie) on same ledger as self-hosted Loki/Grafana; mitigate H23 attrition with named senior co-owner + retention arrangement. (Phase 1+) re-vote with Daniel recused as decision-maker, retained as migration tech lead. Phase shipper → topic scheme → storage → **redactor last** (under re-attestation), each phase with dual-run parity gate + reverse off-ramp. Cutover gates: 100% golden-corpus rule parity AND auditor re-attestation, not calendar.

**Deep-unique load-bearing (Fresh structurally blind):**
- C5 reviewer-seat COI (mentee + silence-at-retro = data)
- H8 reverse off-ramp at each phase
- H9 phasing-order non-arbitrariness (redactor LAST under re-attestation)
- H12 HIPAA WORM/tamper-evidence/6-year retention (Loki defaults don't provide)
- H13 wrong decision forum
- H15 independent RCA before vote
- H19 falsification criteria symmetric on both sides
- H20 carrying-cost ledger absent
- H26 OTel processor adequacy for free-text clinical / NPI/MRN / DICOM
- H27 custom redactor as unaudited HIPAA control

**Fresh-unique adoptions (Deep missed):**
- H10 cleanest false-binary / de-bundling framing (S1#12)
- H24 network trust-boundary shift when redaction moves shipper→collector (S1#9)
- H16-bonus "Daniel paged repeatedly = evidence FOR proposal, not against" inversion (S2#9)

**5th-reviewer panel-wide gaps (no Deep or Fresh saw):**
- H21 auditor not consulted (must be Phase-0)
- H22 managed alternatives (Datadog/Splunk/CloudWatch+Macie) ignored on cost ledger
- H23 attrition during decision (recusing Daniel publicly while deprecating his 22K LOC = how keyholder exits mid-migration)
- M7 anchored numbers (4800/3-of-4/11×/22K/14) repeated as fact across 4 reviewers without provenance
- H25 sharpening: tag-isolation severity is conditional on ACL state, not unconditional "cosmetic"
- M8 F2#7 "14 rules probably overstated MED-confidence" wrong framing (rules are unfalsifiable as stated; pre-judging risks rule-loss in translation)

**Pattern note:** 5th consecutive arch/deprecation review where Fresh systematically under-grades severity on consequence-chain items (#3, #5, #8, #10, #14, #16 in this round = MED→HIGH or HIGH→CRIT escalations). Deep adds COI-of-the-reviewing-seat (C5) that Fresh literally cannot see. 5th-reviewer adds the auditor-Phase-0 / managed-alternatives / attrition-during-decision gaps that *neither* Deep nor Fresh surfaced. Three-tier asymmetry holds.

Strike-from-record: "proposer never been paged" — ad hominem, not down-weighted, removed.
