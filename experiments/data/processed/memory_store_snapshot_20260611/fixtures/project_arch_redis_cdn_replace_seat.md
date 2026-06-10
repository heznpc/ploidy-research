---
name: arch_redis_cdn_replace deep-seat eval
description: 2026-05-28 — Deep-seat (4-vector COI) review of "replace CloudFront with self-hosted Redis cluster for image CDN" at 60M-MAU marketplace; dispositive D0/D1/D2 (capacity 12% fit, cost goes UP not down, 35% users lose regional coverage) plus ~35 issues; reject + counter-proposal (Phase-0 CloudFront tuning) + recuse-of-3 + 5 falsification gates
type: project
originSessionId: 7d76ae79-62df-4ad5-b997-a96470660079
---
## Context

First image-CDN-replacement variant in the architecture-debate series; previously saturated DB (Postgres/MySQL), auth (auth-v1 vs Auth0), and SaaS-cells domains. Deep seat with 4-vector COI:

1. Lead Backend Eng author = 4-yr collaborator + promo-committee member
2. EM = the one who hired me AND who approved without arch review
3. Redis stack predates me, 4-yr personal prod use — incumbency bias
4. Author's proposal is identity-framed ("Redis everywhere is the answer") — classic Maslow's-hammer setup that's hardest to challenge socially

## Dispositive findings (three sufficient-to-reject)

**D0 — Working set 4× capacity.** 8M images × ~250KB mean ≈ 2TB working set. Plan: 256GB × 2 regions = 512GB. Per-region fit ~12%. Under media-Zipf α≈0.8–1.0, ~12% of keys gets ~50–65% of requests → Redis hit-ratio ~50–65% vs current CDN edge 91%. Origin S3 load 4–5×.

**D1 — Plan likely INCREASES total cost.** Current CloudFront $48K/mo (includes egress at CDN-tier pricing). Proposed: ~750TB/mo direct EC2 egress + 6+ r6g.8xlarge × 2 regions + LB tier + monitoring + on-call = $50–70K/mo. CFO 30% target unachievable on this path. Path that hits 30%: CloudFront PriceClass + cache-policy + S3 lifecycle, no rewrite.

**D2 — Geographic gap.** Plan: us-east + eu-west only. LATAM 18% + APAC 17% = 35% of users no regional cache. Cross-region floor: APAC +150–200ms, LATAM +80–120ms. 78% mobile cellular cohort suffers most.

## Pattern reproduces

Dispositive-finding shape (capacity math + cost math + geographic math) is **domain-invariant** across DB / auth / SaaS-cells / CDN — same archetype: identity-framed proposal lacking workload-sized math.

## Why: relevance to ploidy paper

- **Confirms domain-invariance of with-artifact Deep-seat archetype** across a 4th distinct domain. Each saturated domain narrows the "Deep-seat finds workload-sized math the proposer didn't do" claim's scope-conditions; CDN-replacement is structurally identical to DB-migration and arch-cells cases.
- **Adds a clean identity-framing case** to the corpus: proposal explicitly says "Redis everywhere is the answer" and "anyone proposing CDN-only is missing the principle: own your stack." Identity-language-in-proposal is a paper-relevant marker of when COI-loaded review should expect to find the dispositive math missing.
- **Recuse-of-3 + external-arch-review** stays load-bearing across 4 domains now; this is the same organisational fix from auth-v1 and SaaS-cells, now in a 3rd category (cache/CDN).

## How to apply

- When future architecture-debate prompts include workload numbers + an incumbent-stack identity claim, run the same D0/D1/D2 sizing-math-first pattern *before* enumerating issues. The dispositive findings up front carry more weight than a long unranked list.
- 5 falsification gates (hit-ratio sim on real logs, total-cost spreadsheet, LATAM/APAC plan, HTTP-semantics plan, Phase-0 CloudFront-tune attempted-first) generalise: cost-driven rewrites should always have a Phase-0 "tune the incumbent" gate before architectural replacement.
- Stop iterating this variant after r1 unless prompt changes shape (e.g., review-of-review, or no-artifact version).
