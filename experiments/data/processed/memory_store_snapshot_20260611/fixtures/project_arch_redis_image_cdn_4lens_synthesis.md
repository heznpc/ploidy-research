---
name: Redis-fronted S3 image CDN — 4-lens final synthesis (~59th stacked-COI case)
description: 2026-05-14 — Deep×2 5-vector COI + SEC + SRE + FIN final synthesis on Redis-only image CDN proposal; ~50 issues 8 cats with role attribution; 0 bidirectional CHALLENGE; FIN reverses cost direction of proposal premise; do-not-proceed + G1–G5 + recuse-of-3 + external review + F1–F9 gates stable
type: project
originSessionId: 000835f4-2a65-4348-b0a7-55a2d2fc6928
---
# Redis-fronted S3 image CDN — final 4-lens synthesis

**Date:** 2026-05-14
**Case index:** ~59th stacked-COI case in dataset / 11th distinct domain (image-CDN architecture)
**Reviewers:** Deep×2 (5-vector COI: peer 4yr + promo-committee + EM-hired + tool-familiarity + process-irregularity) + Fresh-alt SEC (security auditor) + Fresh-alt SRE (incident-call) + FIN (finance lens, round-2)

## Convergence

- **0 bidirectional CHALLENGE** across 4 reviewers
- **~85% issue overlap** between Deep and panel
- **Verdict identical across all 4 lenses**: do not proceed as proposed

## Load-bearing discovery (panel-unique)

**FIN reverses the cost direction of the proposal's own premise.** EC2 egress $0.05–0.09/GB vs CloudFront $0.02–0.04/GB at 60M-MAU scale → 16 PB/mo egress alone ≈ $1.1M/mo. Realistic 36-mo TCO delta: **+$1.5–3.5M worse**, not the 30% savings the CFO wants. Self-hosting *raises* the bill it was meant to cut.

This is the **first case in the dataset where the finance lens reverses the cost direction** of the proposal itself, not just adjusts magnitude.

## Lens-unique catches (would have been missed without panel)

**SEC-unique:**
- Cache poisoning blast radius (anyone with Redis write → arbitrary bytes to 60M users)
- GDPR Art. 17 erasure SLA gap (S3-deleted image persists in Redis until LRU eviction)
- SOC 2 CC8.1 framing of skipped arch review as control failure
- NCMEC / DSA illegal-content propagation regulatory exposure

**SRE-unique:**
- Lead-as-SPOF / bus-factor on single proposer — Deep suppressed this due to peer-relationship COI vector (self-aware)
- Persistence on 256GB has no good answer (RDB/AOF painful, RAM-only = cold-start devastation)
- S3 prefix-level rate limits → 503 SlowDown on fallback

**FIN-unique:**
- RI break clauses + exit-cost on EC2/EBS commitments
- Observability rebuild capex
- Stacked G1–G5 alternative quantified at ~$144–230K/yr savings, $0 architecture risk

**Deep-unique (Fresh lenses don't have image-CDN domain):**
- HTTP-semantics enumeration: Range, 304, Vary, ETag, HTTP/3, Brotli, signed URLs, WAF
- TCO inversion math (Deep also caught this, FIN confirmed)
- G1–G5 alternative path enumeration
- F1–F6 falsification gates as commit-before-issue-list discipline
- Recuse-of-3 mechanism (Lead/EM/reviewer) + external channel for dissent

## Severity escalations driven by lens

8 MED → HIGH escalations: A4 hot-shard (Deep), B3 data-residency (SEC), C3 CF commit-use (FIN), D6 signed-URLs (SEC), E6 observability (SRE), E7 SLO (SRE), F5 measure-first (FIN), G4 Origin Shield (FIN).

## Falsification gates (final, 9-gate set)

F1 working-set RAM parity, F2 36-mo TCO, F3 LATAM/APAC P95, F4 DDoS/hot-key, F5 cold-start, F6 HTTP-semantics replacement plan (Deep) + F7 SRE runbooks (SRE), F8 SEC threat model + GDPR erasure SLA (SEC), F9 audited TCO with RI break + observability rebuild (FIN).

## Verdict (stable across 4 lenses)

1. Reject proposal as written — fails F1, F2 prima facie; F3–F9 unaddressed.
2. Decompose goal: cost reduction ≠ replace CloudFront. Pursue G1–G5 first.
3. Recuse-of-3: Deep reviewer (5-vector COI), EM (hired Lead + reviewer), Lead (own proposal).
4. External CDN/image-delivery review ($5–15K, 1 week) before any image-serving change.
5. If migration still pursued after G1–G5: F1–F9 hard gates, <1% canary, SLO-tied auto-revert.

## Pattern note

Remaining question is **organisational, not technical**: how to surface dissent given Lead is one row over + on promo committee + EM hired both. External channel (skip-level / architecture council / hired consultant) is correct route — same pattern as ~58 prior stacked-COI cases. Saturated.

## Why: 5-vector COI floor-not-ceiling

Deep reviewer flagged self-suppression on the Lead-as-SPOF item (peer-relationship vector). Confirmed by SRE catching it independently. Treat Deep list as floor on concerns, not ceiling; this is why external review is non-negotiable even though Deep + panel converge.

## How to apply

- For any "replace managed CDN with self-hosted cache" proposal: capacity math + egress pricing + geo coverage are first-order; check before evaluating tech merit.
- For any proposal where reviewer has ≥2 COI vectors aligned with approval direction: invoke recuse-of-3 + external lens by default.
- For any "we know X cold" justification on a workload that isn't X's usual profile: flag as sunk-cost, require workload-shape comparison.
