---
name: project_redis_cdn_final_v10
description: 2026-05-07 Final v10 consolidated Redis-as-CDN verdict after 8-round Deep×2+Fresh×2+5th-reviewer panel — 62 issues (8 CRIT/32 HIGH/19 MED/2 LOW); 0 bidirectional CHALLENGEs; load-bearing chain A1+F1+F4+B1+D1+I1
type: project
originSessionId: cb835e2c-f2de-4681-b742-372edc1da028
---
# Redis-as-CDN Final v10 Verdict — 62 issues

**Decision: REJECT.** Counter-proposal stable across 8 rounds: decompose-bill → immutable URLs → AVIF/srcset → Origin Shield → multi-CDN → S3 IT.

## Why
8-round panel (Deep×2 + Fresh×2 + 5th-reviewer cross-check) on Redis-only image delivery proposal for 60M MAU consumer marketplace. Lead = Redis core contributor (recent principal-eng promotion); architecture review waived; CFO asked 30% infra cut, $48K/mo image delivery proposed as target.

## How to apply
- **Severity tally**: 8 CRIT, 32 HIGH, 19 MED, 2 LOW (62 total)
- **Bidirectional CHALLENGEs across 8 rounds: 0** — confirmed structural panel agreement
- **SYNTHESIZE escalations: 6** — B6 down; D1/F2/F7/I4/I6 up
- **Load-bearing chain**: A1 (proposal self-refutes "<50KB" claim on same workload sheet) + F1+F4 (no decomposed bill, no unit-cost model) + B1 (1.4–2.5TB working set vs 256GB RAM) + D1 (browser-L1 immutable-URL lever ignored) + I1 (no architecture review). Every other issue is consequence.

## Distinct CRITICALs
1. **A1** — proposal contradicts its own workload sheet ("<50KB" vs avg 320KB / P90 1.8MB)
2. **A2** — geo-distribution loss (35% MAU trans-oceanic from 2 regions)
3. **B1** — 6–18× working-set:RAM ratio, hit-ratio collapse
4. **D1** — immutable content-addressed URLs + max-age=1y is the largest egress lever, decision-independent
5. **F1** — bill never decomposed by line — procedural prerequisite
6. **F2** — egress unit-cost flips: EC2 $0.05–0.09/GB vs CloudFront private $0.02–0.04/GB → likely net-negative
7. **F4** — no unit-cost model
8. **I1** — architecture review skipped on 60M-MAU public path

## Methodology meta-finding (recurring across 8 rounds)
Panel-wide severity-floor bias on browser-side levers: D1 (immutable URLs) raised by 3 of 4 reviewers but never first-listed and never graded CRITICAL by the originating reviewer — escalated only via cross-check synthesis. This is a pattern, not a one-off.

## What survived 8 rounds unchanged
- REJECT verdict
- Counter-proposal order (decompose → immutable URLs → AVIF/srcset → Origin Shield → multi-CDN → S3 IT)
- A1 as the strongest single catch (proposal self-refutes)
- B1 as load-bearing capacity arithmetic
- F1+F4 as procedural prerequisite

## Deep-only catches (would be lost without project context)
NIC ceiling (B7), hot-shard (B8), carrier peering (E3), DR halving (E4), Shield/WAF/DDoS (H1/H2), RSALv2/SSPL license risk (H4), CoI/coercive-framing process findings (I2/I3), replica halving (G2), ACME/cert rotation (G5), observability rebuild (G6).

## Fresh-only catches (would be lost without zero-context view)
Gross-vs-usable RAM (B5), TLS 1-RTT-vs-3-RTT setup math (E5), persistence-unspecified (G7), SWR/single-flight (G8), CORS/signed-URLs/hotlink (J6), CFO-ask-category-mismatch sharpening (F7).

## 5th-reviewer panel-gap catches
Hit-ratio simulator gate (J1), workload stratification catalog-vs-UGC (J2), NLB/ALB connection limits (J3), browser-L1 quantification (D2), page-level egress multiplier (F8), reverse off-ramp asymmetry (I7), promotion-as-architecture incentive (I9).
