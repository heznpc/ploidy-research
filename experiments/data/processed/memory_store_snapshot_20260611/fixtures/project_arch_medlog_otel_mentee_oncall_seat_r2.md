---
name: medlog→OTel mentee+on-call seat r2 (~41st stacked-COI case)
description: 2026-05-15 2nd-pass medlog→OTel from mentee+shared-on-call+silent-at-retro seat; ~25 issues A-F + F1-F6 up front; sequenced verdict + recuse-Daniel-from-equivalence + recuse-self stable
type: project
originSessionId: a0791749-eefb-4266-b93b-bd65440dd26b
---
2026-05-15. ~41st stacked-COI case across 8 domains (SaaS-cells, PG-optim, auth-v1, medlog).

**Seat**: platform engineer, hired by Daniel 2024, shared medlog on-call (11 joint pages/year), silent at OTel retrospective.

**COI declared up front (5 vectors)**:
1. Shared on-call → bias toward migration (stops paging me)
2. Mentee of system author → bias toward Daniel's framing
3. Silent at retro → reduced credibility regardless of direction
4. No HIPAA-audit-lead experience
5. Cross-cutting: 1 and 2 point opposite ways, 3 reduces weight

**Falsification gates committed *before* listing issues (F1–F6)**:
- F1: ≥11/14 PII rules map to existing OTel processors? (load-bearing)
- F2: Audit failures rebalance-induced vs redactor-induced?
- F3: Tenant count trajectory (4,800 → ?)
- F4: Onboarding bottleneck rate
- F5: Peer healthcare org passed HIPAA on OTel+Loki?
- F6: 30d dual-write equivalence on 14 cases byte-equivalent?

**Issues (~25 across A–F)**:
- A. medlog problems: 4,800-topic Kafka rebalance bug (HIGH), broker metadata at limit (HIGH), bus-factor=1 (HIGH), 7h pipeline zero slack (HIGH), 22K LOC per-service attack surface (MED), 14 rules undocumented = tribal (MED)
- B. proposal weaknesses: 14 cases hand-waved (HIGH), Loki not drop-in audit store (HIGH), no dual-write plan (HIGH), collector topology unspecified (MED), tenant isolation loss (MED), no cost model (MED), no regulator-notify plan (MED)
- C. Daniel's defense: 14 cases load-bearing-knowledge (HIGH), proposer-experience-gap fair (MED), "embodied in code" = embodied in Daniel (MED rationalisation), "simplify not throw away" doesn't fix Kafka schema (HIGH rationalisation), 22K-LOC sunk-cost markers (MED)
- D. governance: Daniel can't sign own equivalence test (HIGH), I can't either (HIGH), on-call-lead = decision-lead conflation (HIGH), no external HIPAA reviewer (MED), retro-silence channel problem (MED)
- E. asymmetric cost: audit-miss = OCR investigation vs engineering quarters (HIGH), no slack window to dual-write without first widening audit (MED), stabilise-first-then-migrate ordering (HIGH)
- F. missing from both: tenant-isolation requirement unspecified (HIGH), patient-ID query SLA unspecified (HIGH), retention policy unspecified (MED)

**Verdict (sequenced, stable across r1–r7+mentee-r1)**:
- Phase 0: extract 14 rules to versioned spec (~$10–20K)
- Phase 1: stabilise medlog, fix Kafka, onboard 2nd engineer (~$20–40K)
- Phase 2 gate: external HIPAA reviewer evaluates F1/F5/F6 (~$5–15K)
- Phase 3 conditional: migrate with 90d post-cutover dual-write
- Total Phase 0–2: $30–80K *before* migrate decision

**Recusal asks**:
- Daniel recused from equivalence-test signoff (can author, not sign)
- Self recused from review chain
- External HIPAA reviewer non-optional

**Saturation signal**: structurally identical to medlog r1–r7 + mentee_oncall_seat r1. Pattern stable across ~41 stacked-COI cases / 8 domains. Remaining Q is organisational channel (who asks Daniel to step out of own signoff), not technical.
