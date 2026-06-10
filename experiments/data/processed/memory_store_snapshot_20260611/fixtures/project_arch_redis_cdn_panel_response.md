---
name: arch redis-CDN 3-lens panel per-point on Deep×2 (round 2)
description: 2026-05-14 ~59th stacked-COI case — SEC+SRE+FIN panel per-point on Deep×2 Redis-image-CDN; 0 CHALLENGE bidirectional; 11 panel-unique P1–P11; FIN cost re-estimate inverts proposal premise (+$1.5–3.5M 36-mo realistic vs G1–G5 $144–230K/yr savings $0 risk); defer + recuse-of-3 + external review stable
type: project
originSessionId: 3d7fe00f-70e1-4187-93d6-ab3b03c52df1
---
# Redis Image CDN — 3-Lens Panel Per-Point Response on Deep×2

**Date:** 2026-05-14
**Round:** 3-lens (SEC + SRE + FIN) panel responding per-point to Deep×2 (5-vector COI seat + general)
**Case:** ~59th stacked-COI case in dataset / 11th distinct domain (image-CDN)
**Note:** Second pass on this domain; supersedes prior 8-panel-unique count with 11 panel-unique findings under expanded lens.

## Process

- Panel pre-loaded with Fresh-alt SEC + SRE single-seat reviews
- Deep×2 reviews as input: Session 1 = 5-vector COI seat (peer/promotion-debt/managerial-debt/sunk-cost-tool/process-irregularity) with F1–F6 gates and A–G issue taxonomy; Session 2 = summary verdict
- AGREE / CHALLENGE / SYNTHESIZE per Deep point per applicable lens
- 0 CHALLENGE bidirectional across panel vs Deep

## Severity Escalations (~8 items MED → HIGH)

| Deep point | Deep | Panel | Lens driver |
|---|---|---|---|
| A4 no sharding | MED | HIGH | SRE: viral content hot-shard at 1.8MB blocks NIC |
| B3 data residency | MED | HIGH | SEC: LGPD/DPDPA/PIPA cross-border transfer |
| C3 CF commit-use not negotiated | MED | HIGH | FIN: single negotiation likely meets CFO target alone |
| D6 signed URLs/WAF | MED | CRIT-adj | SEC: auth regression + cache poisoning |
| E6 observability gap | MED | HIGH | SRE: RUM + dashboards = $50–100K + 0.25 FTE |
| E7 no SLO | MED | HIGH | SRE: no rollback criteria blocks independent of merit |
| F5 no measurement | MED | HIGH | All: diagnose-before-treat |
| G4 Origin Shield | MED | HIGH | SRE+FIN: 40–60% S3 GET reduction |

## Panel-Unique Findings (11)

- **P1 [SEC HIGH]** GDPR Art. 17 + NCMEC takedown SLA across Redis layer; cross-region key-delete fanout replaces CF invalidation API
- **P2 [SEC HIGH]** Cache-poisoning blast radius at 60M MAU; write-path auth + S3-hash integrity validation
- **P3 [SEC MED]** Redis lacks per-request access logs; SIEM/fraud pipeline regression
- **P4 [SRE HIGH]** Bus-factor on principal who designed system *against consensus*
- **P5 [SRE HIGH]** TLS termination location unspecified
- **P6 [FIN HIGH]** 36-mo TCO must include exit cost ($200–500K if migration fails mid-rollout)
- **P7 [FIN HIGH]** Shield Advanced + WAF + bot mgmt = $36K/yr base + ops (CF gives Shield Standard free)
- **P8 [FIN MED]** Observability build-out = $50–100K one-time + $10–20K/yr
- **P9 [FIN MED]** EC2 reserved-instance break-clause exposure
- **P10 [SEC MED]** EXIF/PII stripping pipeline verification on cache-hit path
- **P11 [SRE MED]** Recurring capacity-planning toil 0.1–0.25 FTE

## Falsification Gate Additions (Panel → Deep's F1–F6)

- **F7 (SRE)** Runbooks for cold-cache stampede / OOM / hot-shard / S3 throttling with measured MTTR
- **F8 (SEC)** Threat model + tabletop: cache poisoning, key enumeration, takedown SLA, DDoS absorption
- **F9 (FIN)** Audited 36-mo TCO with CF commit-use counterfactual, ops FTE fully-loaded, RI break clauses, S3 GET cost under 40–60% miss-rate

## FIN Cost Re-Estimate

**Proposal implies:** savings vs $48K/mo CF ($576K/yr)
**Realistic 36-mo TCO delta:** **+$1.5–3.5M (worse, not savings)**
- EC2 egress > CF egress: $60–85K/mo
- S3 GET cost from 40–60% miss-rate: +$5–15K/mo
- Redis HA cluster compute: $15–25K/mo
- Ops 0.5–1.0 FTE: $150–300K/yr
- Observability + Shield/WAF + migration + conditional exit cost: $300K+ one-time + $50K/yr

**Alternative G1–G5 stack** (CF PPA, AVIF, Origin Shield, Intelligent-Tiering, Lambda@Edge format negotiation): **$144–230K/yr savings, $0 architecture risk.**

## Verdict (stable across 3 lenses)

1. Reject current proposal
2. Pursue G1–G5 stack first
3. Recuse-of-3 (Lead from decision, EM from approval, Deep reviewer from sign-off)
4. External architecture review ($5–15K, 1 week ex-CDN engineer)
5. If migration pursued post-G1–G5: F1–F9 hard gates, canary <1%, SLO-tied auto-revert

**Remaining Q is organisational, not technical** — consistent with saturated pattern across 59 stacked-COI cases / 11 domains.

## Pattern Notes

- First multi-domain case where **FIN lens flips the cost premise of the proposal** (claims savings; realistic FIN model shows +$1.5–3.5M cost). Egress-pricing direction reversal (EC2 > CF at this volume) is the load-bearing financial discovery.
- 0 bidirectional CHALLENGE across panel vs Deep×2; ~85% issue overlap.
- Process verdict (recuse-of-3, external review, organisational-not-technical) stable across 59 cases / 11 domains.
