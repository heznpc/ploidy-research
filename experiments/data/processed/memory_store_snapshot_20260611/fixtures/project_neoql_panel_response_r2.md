---
name: NeoQL panel response r2 (SEC+SRE+FIN per-point on Deep×2)
description: 2026-05-15 — ~66th case — 2nd SEC+SRE+FIN per-point pass on Deep×2 NeoQL adoption; 0 CHALLENGE, ~7 SYNTHESIZE, 13 panel-unique items P1–P13; F7–F10 added (10 gates total, 0/10 met); defer + Postgres+dbt default + recuse-of-3 stable
type: project
originSessionId: f6698f0a-c635-4d59-8c57-2d13ca26a4ca
---
# NeoQL panel response r2 (SEC+SRE+FIN on Deep×2)

Date: 2026-05-15
Case: ~66th case in stacked-COI / panel cross-review dataset (r1 prior).
Inputs: Deep×2 (S2 = full A–G + COI + F1–F6; S1 = saturation note). Fresh-alt×2 (SEC 17, SRE 16).

## Convergence metrics

- **0 / ~47** bidirectional CHALLENGE.
- **~7 SYNTHESIZE** (F3 tightened to 1.5× p50 / 2× p99 ceiling; A3 promoted CRIT via no commercial backstop; A5 promoted CRIT pre-contractor; C2 promoted CRIT; B1/B5 sharpened with plan-stability + plan-freezing; F6 sharpened to ≥3 of 12 + planted-regression).
- **~33 AGREE** across A–G.

## Panel-unique items (P1–P13)

- **P1 [SEC CRIT]** Tenant isolation undefined; cross-tenant leak = highest blast radius.
- **P2 [SEC HIGH]** Recursive CTE codegen = DoS primitive.
- **P3 [SEC HIGH]** No SBOM / signed releases / reproducible builds.
- **P4 [SEC MED]** SAST / SQL-lint bypass.
- **P5 [SEC MED]** Contractor as supply-chain vector.
- **P6 [SEC MED]** Audit-log source-mapping.
- **P7 [FIN CRIT]** TCO ~$570K–$1.1M vs dbt baseline ~$30–60K. Buckets: learning tax, contractor, office trip, parallel SQL fallback, ~3 forced migrations, observability custom build.
- **P8 [FIN HIGH]** No paid support tier / SLA.
- **P9 [FIN HIGH]** Revenue-at-risk during launch uncalculated.
- **P10 [FIN MED]** Enterprise sales blocker via vendor questionnaires.
- **P11 [SRE HIGH]** Plan stability across stats refresh.
- **P12 [SRE MED]** No query-plan freezing.
- **P13 [SEC HIGH]** Code-review-as-security-control degraded.

## Panel falsification gates F7–F10 (added to Deep's F1–F6 = 10 total, 0/10 met)

- **F7** Published security disclosure + signed releases + 3rd-party codegen audit.
- **F8** Tenant-isolation property-based test suite.
- **F9** TCO model showing NeoQL < dbt/PRQL baseline.
- **F10** Vendor-risk-review sign-off.

## Verdict (stable)

Defer. CRIT confidence. Default = Postgres + dbt (or PRQL). Re-evaluate at NeoQL v1.0 + ≥1 verified prod reference deployment + paid support tier. Recuse-of-3 + external senior data eng chosen by the 2 unconflicted engineers (not the lead). Unbundle into 3 separate votes (adopt / contractor / office-visit).

## Pattern note

~66th stacked-COI / panel cross-review case overall. r1 and r2 converge on identical verdict with overlapping but non-identical panel-unique surfacing. Remaining question is organisational channel (who chairs unconflicted decision), not technical. Stop iterating further panel passes on NeoQL.
