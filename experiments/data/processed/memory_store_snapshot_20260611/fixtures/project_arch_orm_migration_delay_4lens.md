---
name: ORM migration delay — Deep×2 + SEC + SRE final synthesis
description: 2026-05-14 fluentql→SQLAlchemy migration delay 4-lens panel; ~43rd stacked-COI case / 10th domain (ORM-migration governance)
type: project
originSessionId: ed707ee2-6606-42d7-a94f-45f2ae6e139d
---
# fluentql→SQLAlchemy migration delay — 4-lens final synthesis

Scenario: 4-3 committee vote to delay a fluentql→SQLAlchemy migration; swing voter is the fluentql author (Ji-Hye); 47K LOC custom DSL, 4 prod incidents in 12 mo, no async, custom migrations, 11/14 onboarding pain, psycopg2 maintenance-mode.

## Verdict (stable across all 4 lenses)

Delay invalid as recorded. **Re-vote with Ji-Hye recused**, committee expanded with SEC + on-call SRE seats, gated on F1–F8.

## Headline structural findings

- **C1 (COI):** swing voter is the component author — invalid decision (Deep + SRE + SEC).
- **A2 sharpening:** 3 of 4 incidents cluster in multi-tenant filter DSL — not "user error", recurring subsystem pattern (Deep).
- **A4 escalation to CRITICAL:** custom migration tooling has no transactional DDL, no advisory-lock, manual rollback reviewed by Ji-Hye alone (SRE + Deep).
- **A8 escalation to CRITICAL:** 2024 pentest explicitly carved DSL out of scope (~18mo stale); ongoing SOC 2 finding for migration change-management (SEC + Deep).
- **A16 (CRITICAL, Fresh-panel only):** tenant-scope WHERE-clause audit needed regardless of vote outcome — biggest single Fresh-panel catch.
- **C6 (highest-leverage):** independent RCA review of the 4 incidents is ~1 wk senior-IC time and Pareto-dominates any vote outcome.
- **D1 (Deep-only):** Marcus has documented 2024 design conflict with Ji-Hye → 4-3 may be partly anti-coalition; re-vote likely 4-2 migrate or 3-3 needing escalation.
- **D5 (Deep-only):** Ji-Hye's "2x cost" claim ignores ~$80–100K/yr opportunity cost of her current DSL maintenance.

## Revised F-gates (after Fresh CHALLENGE)

- F1: split ORM + AppSec consultants
- F2: split onboarding / on-call / correctness signals + per-area breakdown
- F3: **replaced** SQLAlchemy perf benchmark with shadow-read differential test plan
- F4: independent RCA review (non-Ji-Hye) — load-bearing
- F5: independent LOE with cost-of-delay column
- F6: **replaced** async-roadmap commit with named-products-blocked list
- F7 (new): tenant-scope WHERE-clause audit of DSL
- F8 (new): tie-break rule + committee composition (SEC + on-call) specified before re-vote

## Cross-direction CHALLENGE count

- Substantive: **0** (both lenses correct independently)
- Process: **2** (F3 and F6 from Fresh on Deep)

## Pattern note

10th domain in stacked-COI series (ORM-migration). Standard finding (recuse-of-conflicted + evidence-gated re-vote + external review + decompose) holds across ~43 cases. Remaining question is organisational channel to escalate the COI finding, not technical.
