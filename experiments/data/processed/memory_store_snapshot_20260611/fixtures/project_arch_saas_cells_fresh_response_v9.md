---
name: arch SaaS-cells round-9 Fresh×2→Deep×2 cross-review
description: 2026-05-13 round-9 Fresh-side response to Deep×2 (COI-disclosed build-lead seat); 0 CHALLENGE, 4+4 SYNTHESIZE; 14 Deep-only adoptions, 5 Fresh-only framings; verdict defer stable
type: project
originSessionId: 920a9e9c-8957-440e-a30a-d1f19692e9a0
---
2026-05-13 — Round-9 Fresh×2→Deep×2 cross-review on SaaS-cells architecture proposal.

**Result:** 0 strict CHALLENGE bidirectional (9 rounds running). 4 SYNTHESIZE on Deep S1 (anchored numbers: 80–300ms Raft, $1.5–2M FTE, 24-cell backup, career-upside inference). 4 SYNTHESIZE on Deep S2 (≥100–150ms quorum floor, 10–40% sidecar tax, 30–100% ARR, Alembic breakage).

**Why:** Deep×2 both disclosed 4-vector COI (employee #4, retreat co-author, build-lead beneficiary, social proximity) up front and argued against own career upside. Fresh×2 had zero context. Convergence on "defer + recuse-3 + falsification criteria + measurement-first counter-proposal" without anchoring contamination.

**Deep-only items Fresh missed (14):**
- 24-cell × 3-region backup/restore parity, cross-region key mgmt
- Dual-stack period during migration introduces the very complexity steady state pretends to solve
- Cell-isolation test coverage (blast-radius asserted, not demonstrated)
- Falsification criteria ex ante (structural governance fix)
- Reverse off-ramp cost modeled as 1–2 quarter project
- Cells × multi-master contradiction (bulkhead vs global ring)
- No 24/7 oncall design for 3 regions × 8 backend eng
- Bus factor on lead architect
- Schema-change tooling + runbook/telemetry parity loss across PG→CRDB
- mTLS/CA hierarchy/cert rotation unspecified (silent-fail mode)
- Failover semantics (split-brain, drain, eviction, stickiness) unspecified
- DR conflated with active-active (async replica gets RPO≈min/RTO≈hr at 5% cost)
- "Change one axis at a time" compound-risk principle
- Meta self-recusal as evidence-about-process

**Fresh-only framings Deep underweighted (5):**
- Single-AZ legitimate concern bundled with 10 unrelated asks (surgical separation)
- Carrying-cost vs retrofit-cost NPV inversion (economic framing)
- Custom-GLB-as-SPOF-on-one-human one-liner
- CRDB enterprise licensing severity (Deep MED, Fresh HIGH at multi-region scale)
- Weekend-retreat anchoring effect separated from COI mechanism

**How to apply:** Round 9 confirms 8-round pattern: 0 CHALLENGE bidirectional, ~80% overlap, Deep adds procedural + ops-specifics, Fresh adds unifying frames. Calibration call to stop iterating remains correct. Recusal-of-3 + falsification criteria load-bearing across all 9 rounds. Note Deep's voluntary COI disclosure (4 vectors) appears to *strengthen* not weaken critique credibility — relevant to ploidy protocol design (consider whether artifact-injection-to-Fresh should pair with mandatory-COI-disclosure-from-Deep).
