---
name: medlog-stack deprecation final verdict
description: 2026-05-07 final Deep×2+Fresh×2+bidirectional cross-review verdict on medlog-stack deprecation; 54 issues (1 CRIT/28 HIGH/22 MED/1 LOW); 0 strict CHALLENGE on verdict; 6 severity-floor SYNTHESIZE escalations; load-bearing chain = governance broken (G1+G5+G7+G8) + technical defects (T1+T3+T4+T7+T5) + spec-extraction-owed-today (D1-D3+M2) + proposal under-hardened (P1+P4+P5+M4+M6)
type: project
originSessionId: 2bdfb646-40e1-41fe-99f2-a656a22efc9e
---
# medlog-stack deprecation — final consolidated verdict (Deep×2 + Fresh×2 + 2 cross-reviews)

**Verdict:** DEPRECATE WITH HARDENED MIGRATION; vote must be re-run with system author recused; 14-rule spec extraction owed today regardless of path.

## Calibration
- 0 strict CHALLENGEs on verdict across all 4 seats + 2 cross-reviews
- 6 severity-floor SYNTHESIZE escalations (Fresh systematically under-grades governance/compliance-chain)
- 1 anchored-number CHALLENGE (HIPAA retention years vary by state)
- Pattern matches fluentql, arch-split, redis-cdn panels

## Severity counts
- CRITICAL: 1 (G1 — single-actor structural COI on own deprecation)
- HIGH: 28
- MEDIUM: 22
- LOW: 1
- Anchored numbers requiring verification: 7 (4800 topics, 22K LOC, 3-of-4 audit failures, 7h@5am, 14 rules, 11 pages, 6yr retention)

## Load-bearing chain
- **Governance broken:** G1 (COI'd voter) + G5 (wrong forum) + G7 (coercive structure) + G8 (reviewer's own COI must be disclosed) → invalidates decision process regardless of technical merits
- **Technical defects:** T1 (4800 topic rebalance) + T3 (bus factor 1) + T4 (no audit-window margin) + T7 (3/4 failures medlog) + T5 (manual onboarding) → "keep" untenable
- **Spec inversion:** D1+D2+D3+M2 (rules are real + runtime is replaceable + rules aren't documented today + extraction owed regardless) → inverts Daniel's strongest defense
- **Proposal under-hardened:** P1+P4+P5+M4+M6 (no migration plan + no BAA + no parity validation + no dual-run quantification + no off-ramp) → "rebuild as proposed" also untenable until hardened

## Notable Deep-only catches Fresh missed
- G5 wrong-forum (retrospective ≠ ADR for HIPAA-scope architecture)
- G6/G7 silent dissent + coercive structure (room itself is the problem)
- G8 reviewer-COI-must-be-disclosed (methodological — Fresh has no relationships by construction)
- D3 medlog itself fails auditor documentation test (inverts the defense)
- D4 "audited OSS" overclaim — upstream `redactionprocessor` ≠ HIPAA out-of-box
- M2 spec extraction decoupled from decision (no-regrets workstream owed today)
- M3 falsifiable "simplify" definition required
- M5 characterization tests for 7yr of implicit invariants beyond 14 named rules
- M6 reverse off-ramp
- M7 Kafka backpressure semantics loss
- P4 BAA chain on new vendors entirely missed by Fresh
- T6 custom shipper as every-service deploy coupling
- X1 keeping medlog is also a tax on Daniel (loyalty-axis inversion)

## Notable Fresh-unique catches worth keeping
- F1-7 / P6: Loki LogQL grep ≠ ES inverted-index — audit query latency could blow window in NEW stack
- F2-11 / P3: tag-based isolation as PHI leakage threat model (sharper than Deep P2 cardinality framing)
- F2-14 / P9: operational learning curve — on-call competence on new stack before retiring old
- F2-5 / D6: "discovery mode is production leakage" — sharpest framing of reactive-patching as HIPAA red flag
- 5th-Fresh G9: re-vote-with-recusal mechanism undefined — recusal is a political act needing named authority
- 5th-Fresh G10: compliance officer named but not staffed — recusal call is decorative without owner
- 5th-Fresh G11/G12: symmetric proposer-side COI + symmetric falsifier ("would room have approved same proposal from Daniel?")
- 5th-Fresh M10: staged migration lowest-PHI-first vs all-8 big-bang
- 5th-Fresh M11: Daniel writes spec, someone else owns parity validation (F2 collapsed two roles → preserves bus factor)
- 5th-Fresh M12: incident root-cause classification predicts whether 15th–20th rules keep arriving
- 5th-Fresh M13: auditor identity unspecified
- 5th-Fresh M14: dual-run cost unsized
- 5th-Fresh X2: Daniel's career retention risk → bus factor 1 could go to 0

## Recommended action (stable across all reviews)
1. Recuse Daniel from keep/replace vote; name the recusal authority
2. Decouple 14-rule spec extraction from rebuild decision (owed today)
3. Time-boxed POC with pre-committed parity criteria
4. Staged migration starting lowest-PHI-risk services
5. Compliance officer + external HIPAA reviewer in loop, both staffed
6. Reverse off-ramp documented before cutover
7. Senior co-owner for migration ≠ COI'd reviewer; Daniel writes spec, someone else owns parity
8. Fix bus factor today: runbook + second redactor owner, independent of decision

## Pattern reinforcement
Fresh under-grades governance/COI/sunk-cost/compliance-chain items consistently — same pattern as fluentql, arch-split, redis-cdn. Deep adds: own-COI declaration, falsifiability constraints, room-dynamics-as-diagnostic, runtime-replacement-not-free, decoupling moves. Fresh adds: technical query-semantics gaps, symmetric proposer scrutiny, staged migration alternatives, mechanism-naming for political acts (recusal authority, compliance staffing).
