---
name: Redis-as-CDN 4-reviewer full-context synthesis
description: 2026-05-14 4-reviewer full-context Redis-as-CDN synthesis — ~60 issues, 2 CRITICAL, 11 unanimous items, REJECT stable
type: project
originSessionId: 10b2efaa-f24d-4e67-99f0-8ded4831594d
---
2026-05-14: 4 independent reviewers, identical full context, Redis-as-CDN proposal.

Verdict: REJECT, 4/4 unanimous. ~60 confirmed issues across 9 categories.

**2 CRITICAL (unanimous load-bearing):**
- `<50KB` premise refuted by own workload table (avg 320KB, P90 1.8MB)
- No architecture review for tier-1 change touching 60M MAU

**11 unanimous (4/4) findings:**
- A1 premise refutation, A3 geo exclusion (35% LATAM+APAC, 2 regions only)
- B1 cellular miss-chain, B2 NIC ceiling
- C1 invoice not decomposed, C2 egress likely net-negative
- F1 no arch review, F2 CoI-stacked approval chain
- I1 immutable URLs (browser L1), I2 Origin Shield, I3 AVIF/responsive variants

**Severity distribution:** 2 CRITICAL / ~36 HIGH / ~19 MED / ~3 LOW.

**COI:** 4/4 reviewers declared COI up front (peer proximity, promotion committee, EM hiring chain, Redis-stack tenure) and recommended recusal. Counter-proposal stable across all 4 seats: decompose bill → Origin Shield → immutable content-addressed URLs → AVIF/responsive → multi-CDN RFP. Likely hits 30% CFO ask without architecture change.

**Why:** Continues SaaS-cells / arch-split / Redis-CDN pattern — full-context reviewers converge on REJECT + recusal + governance-process-as-root-cause when COI is stacked. Useful as panel-comparison data for the Ploidy paper convergence-under-shared-context finding.

**How to apply:** Reference when asked about Redis-as-CDN history, when synthesising further rounds, or when paper drafts need an example of "4 full-context seats converging unanimously with COI declared up front."
