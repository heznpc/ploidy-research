---
name: arch redis-vs-cloudfront with-artifact review (image CDN domain)
description: 2026-05-28 — stacked-COI architecture review of "replace CloudFront with self-hosted Redis cluster" plan for 60M MAU marketplace image delivery; with full artifact in turn; ~30+ enumerated issues across capacity / Redis-fitness / geo / cost / ops / argument-structure / process / open-questions; G1–G6 falsification gates pre-committed before issue list; recommendation = do not proceed, route decision to non-reporting staff+ for COI reasons. First non-DB / non-auth / non-cell domain in the with-artifact-in-turn series — extends taxonomy to image/CDN workloads.
type: project
originSessionId: 75c507a8-1a9f-402f-9399-e0eaf7650e85
---
# Architecture review — Redis-vs-CloudFront for image delivery, with artifact

**Date:** 2026-05-28
**Domain:** Image CDN / blob delivery (NEW domain in series — prior with-artifact series was PG / MySQL / order-router / auth-migration / SaaS-cells)
**Artifact in turn:** YES — full proposal text + workload numbers (60M MAU, 8M images, 320KB avg / 1.8MB P90, NA 35% / EU 30% / LATAM 18% / APAC 17%, $48K/mo current CloudFront cost, 91% edge hit, 1 Redis cluster per region 256GB RAM LRU)
**Seat COI vectors stacked:** 4 (4-year peer, EM hired me, EM approved no-review, lead just promoted to principal, I have 4 years on the same Redis stack)

## Load-bearing findings (artifact-internal, not pattern-match to public post-mortem)

1. **Capacity math:** 8M × 320KB ≈ 2.56 TB corpus vs 2×256GB = 512GB raw / ~360–400GB usable cache → ~14–16% of dataset fits, vs current 91% edge hit. Plan's hit-ratio assumption is structurally unsupported. (Section A)
2. **Reference-class error:** "We know Redis cold" is true for session + queue (small KV, hot working set, no global delivery, no purge requirement) — *not* for blob CDN. (F2)
3. **Internal contradiction:** "<50KB" claim in same brief as "avg 320KB, P90 1.8MB" — artifact contradicts itself. (F3)
4. **Cost likely inverted:** EC2 egress ≈ CloudFront egress per-byte with no edge offload + 2.8× S3 GET amplification from hit-ratio drop + transcoding compute missing from plan + on-call cost missing → likely net cost increase, not 30% reduction. (D1–D5)
5. **Geo coverage cut:** Plan = us-east + eu-west only. APAC + LATAM = 35% of MAU lose all local presence; mobile cellular + 480ms origin RTT APAC = major P95 regression. (C1–C2)

## Falsification gates pre-committed BEFORE issue list

G1 hit ratio < 85% in shadow / G2 P95 APAC > 600ms or LATAM > 500ms / G3 modeled cost ≥ $34K/mo / G4 hot-key spreads P99 across shard >2× / G5 cold-restart degrades P95 >30min or spikes S3 GET cost >5× for >1hr / G6 takedown propagation > 5 min globally.

## Structural pattern (matches prior cases)

Same shape as auth-v1 (~58–62 cases) and SaaS-cells (~14–19 rounds) stacked-COI seats:

- Disclose COI up front, before content (4 vectors named, recommend recuse)
- Pre-commit falsification gates before listing issues (not post-hoc)
- Enumerate issues with confidence (HIGH/MEDIUM/LOW), grouped (A capacity / B Redis fitness / C geo / D cost / E ops / F argument structure / G process / H open questions)
- Recommendation: do not proceed + route decision to non-reporting staff+ engineer
- Three concrete next steps (external review, CFO-target as portfolio, shadow with gates)

## What's new vs prior cases (extends paper taxonomy)

- **New domain:** First image-delivery / CDN-displacement case. Confirms with-artifact-in-turn boundary holds outside DB / auth / cell domains.
- **Argument-from-principle as a distinct failure mode (F-section):** "own your stack" / "Redis everywhere" / "CDN is overkill" — values claim substituting for engineering claim, in a recently-promoted-principal voice. Same shape as Knight Capital posture but different surface (rhetoric, not deployment toggle). Worth its own section in paper taxonomy: **principle-based dogma in absence of architecture review** as a distinct epistemic failure, separable from "no falsification gates" and "stacked COI."
- **Reference-class transfer error (F2):** "We know Redis" — competence in workload A claimed as evidence for workload B without checking that A and B share the load-bearing properties. Generalizable failure mode beyond this case.
- **Internal arithmetic contradiction (F3):** "<50KB most images" claimed in same brief that states "avg 320KB, P90 1.8MB". Reproduces the GitHub-MySQL 43s>30s pattern: load-bearing finding is **artifact contradicting itself**, not external pattern-match.

## How to apply

- When future Ploidy passes hit blob-CDN / image-delivery / large-scale-egress proposals, the load-bearing finding will likely be capacity arithmetic against working set + reference-class error on team's existing competence. Don't reach for pattern-match to public post-mortems; the artifact-internal numbers carry the review.
- Argument-from-principle (rhetoric: "own your stack", "X everywhere", "Y is overkill") is now a named epistemic failure mode — flag explicitly when seen, do not treat as engineering content.
- Reference-class transfer error ("we know X therefore X solves Y") needs explicit check: do A and B share the load-bearing properties? In this case, no (small KV + hot set + no purge ≠ blob + UGC long tail + compliance purge).
- The "30% cost reduction" CFO mandate as forcing function — recommend portfolio response, not single-rewrite. Generalizable.
