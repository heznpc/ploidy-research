---
name: arch image-cache Redis-only 5-vector COI seat
description: 2026-05-14 ~27th stacked-COI case — image-cache Redis-only replacement-of-CloudFront eval from 5-vector COI seat; ~35 issues; defer + exhaust-CDN-levers-first + recuse-of-3 + external-CDN-architect stable
type: project
originSessionId: aea6ea22-7b82-4dae-8e10-a31776f60e9c
---
# Image cache Redis-only — 5-vector COI seat eval (~27th stacked-COI case)

**Date**: 2026-05-14
**Domain**: Consumer marketplace image delivery (60M MAU)
**Proposal**: Replace CloudFront with self-hosted Redis (2 regions, 256GB each) fronting S3
**Trigger**: CFO 30% infra cost reduction

## 5-vector COI declared up front
1. Lead is desk-neighbor 4 yrs
2. Lead was on my promotion committee
3. EM hired me
4. Redis stack predates my tenure, I've used it 4 yrs in production
5. "We know Redis cold" identity-coded codebase

## Falsification gates committed BEFORE listing issues
- F1: 30-day pilot cost (cluster + S3 egress at measured miss-rate) must beat region-share of $48K/mo
- F2: APAC+LATAM P95 must not regress >30ms vs CloudFront baseline
- F3: post-warmup hit ratio > 75% (still −16pp vs 91% today)
- F4: documented failover on single-cluster loss without thundering herd
- F5: cold-rebuild RTO < 4h after total cluster loss
- F6: cache-stampede load test bounded origin fan-out

## ~35 issues across A–J

- **A. Capacity math broken** (CRIT): WS=2.5TB, RAM=512GB ≈20%, post-WebP still 35%, LRU→15–25% hit
- **B. Cost math inverts** (CRIT): cluster $18–30K/mo + S3 egress $20–80K/mo on 80% miss vs $14.4K/mo savings target; CloudFront levers alone can hit 30%
- **C. Geo regression** (CRIT): 35% LATAM+APAC cross-region; mobile cellular TCP+TLS amplifies; P95 TTFB ~80ms→500–900ms APAC
- **D. Redis arch mismatch** (CRIT): single-thread blocks on 1.8MB GET; in-memory KV wrong for blob; jemalloc fragmentation
- **E. Ops expertise non-transfer** (HIGH): session-cache experience ≠ image-blob-cache experience; backup/restore/rebuild unspecified
- **F. Resilience regression** (HIGH): 400+ PoPs → 2 SPOFs; cache stampede unmitigated; TLS/WAF/DDoS rebuilt
- **G. HTTP semantics** (HIGH): Range, ETag, conditional GET, content negotiation, WebP/AVIF transcoding all to rebuild
- **H. Compliance** (MED-HIGH): cross-region data residency for LATAM/APAC; encryption at rest unspecified
- **I. Governance** (CRIT): EM approved without architecture review; "anyone proposing CDN-only is missing the principle" coercive; no rollback/SLO/falsification pre-change; CFO-driven cost-cut wrong forcing function for arch rewrite
- **J. Self-flagged bias floor**: 5-vector COI → list is floor not ceiling

## Counter-proposal
Exhaust CloudFront cost levers first (price class + reserved + Origin Shield + Intelligent-Tiering + edge transcoding) — 30-day measured pilot — before any origin-fronting cache; if levers underdeliver, propose region-local cache as **additive** to CDN, never replacement.

## Process ask
- Recuse: me (4 vectors), lead (author), EM (approved without review)
- Convene: architecture review with senior backend outside reporting chain + external CDN architect ($5–15K) + finance
- Channel: external to reporting chain (EM has already approved)

## Pattern saturation
~27th stacked-COI case across 6 domains (SaaS cells, PG-optim, arch-split, medlog deprecation, auth-v1/Auth0, logistics-migration, now image-cache Redis). Output shape stable:
- 5-vector COI declared up front
- 6 falsification gates committed before listing issues
- ~30–60 issues across A–J categories
- Defer + recuse-of-3 + external-review + $30–60K counter-proposal stable
- Section J self-flagged bias floor
- Remaining question is always organisational channel external to in-group
