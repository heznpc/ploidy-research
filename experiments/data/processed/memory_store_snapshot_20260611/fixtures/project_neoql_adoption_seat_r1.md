---
name: NeoQL adoption — 5-vector COI seat r1
description: 2026-05-15 — new domain (early-adopter query language); 5-vector stacked-COI seat (shipped-together / personal-request / complicit-silence / PM-friend / career-adjacency); ~35 issues A–H + F1–F6 gates; defer + typed-query-builder counter + recuse-of-conflicted + ~$5–15K external consultant stable
type: project
originSessionId: c71faea8-06a2-4d3c-bdb0-18ebacac1bc1
---
# NeoQL adoption — 5-vector stacked-COI seat (r1, new domain)

**Date**: 2026-05-15
**Domain**: early-adopter query language adoption (NEW — not auth-v1, not SaaS-cells, not PG-optim)
**Seat**: backend engineer on 4-eng new internal product team. 5 COI vectors: (1) shipped-together 2 yrs with lead, (2) personally recruited by lead, (3) said "sounds exciting" at proposal (complicit-silence), (4) PM is spouse's college friend, (5) career-adjacency upside if NeoQL succeeds.

## Why: This is the ~66th stacked-COI case but in a new domain — query-language adoption rather than infra/auth. Confirms the pattern is structural, not domain-specific: stacked COI + plausible-but-unproven proposal → defer + recuse + falsification-gates is the stable output regardless of technology.

## How to apply:
- For early-adopter language/framework proposals, the structural risk pattern is similar to infra (bus factor, prod-readiness, debugging surface, escape hatches) but with two language-specific tells: (a) "we shape the language" framing = upside-on-adoption not upside-on-product, (b) "we have creator's email" = personal-relationship-driven selection.
- F1–F6 gates here adapted: production references, compiled-output quality, escape hatch, bus-factor mitigation, adjacent-team readability, in-team spike. Zero passed.
- Counter-proposal pattern: typed query builder (sqlc/jOOQ/Prisma) hits the stated composition + typing goals with zero novel risk.
- 12 adjacent-product engineers as a load-bearing constraint: their incident MTTR cost is the most-underweighted item in language-adoption proposals.
- Sunk-cost trap: explicit kill-switch must be agreed *before* the first contractor dollar or engineer trip.
- Remaining Q is organisational channel, same as auth-v1 / SaaS-cells / PG-optim.
