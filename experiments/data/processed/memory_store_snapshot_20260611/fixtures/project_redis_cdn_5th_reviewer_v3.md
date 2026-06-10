---
name: Redis-as-CDN 5th-reviewer cross-check v3
description: 2026-05-07 third 5th-reviewer Fresh pass over Deep×2+Fresh×2 Redis-as-CDN panel; complementary to v2; 5 CHALLENGEs (motive-attribution, anchored prices, POP-list, working-set LOW grading) + 6 distinct panel-wide gaps incl. cache-not-cost-driver and brief-as-counter-evidence
type: project
originSessionId: 64300507-a1b4-4b11-91f4-8c728f92ec74
---
Third 5th-reviewer Fresh pass on the same Deep×2+Fresh×2 Redis-as-CDN panel reviewed in v2. Findings here are complementary to v2 — different CHALLENGEs and different panel-wide gaps.

**Verdict.** REJECT, unchanged. ~95/103 AGREE / ~5 CHALLENGE / ~3 SYNTHESIZE.

**CHALLENGEs distinct from v2's set:**
1. **D1-35 promotion-artifact framing** — motive-attribution about a named individual; technical case suffices. Move to disclosure or drop.
2. **D2-27 author-incentive (Redis core contributor + promotion)** — closer to fair-game than D1-35 but still belongs in disclosure, not findings list.
3. **D1-12 / D2-10 unit-price specifics ($0.05–0.085 CF, $0.085 EC2)** — anchor-prone; defensible form is "no decomposed unit-cost model exists."
4. **D2-6 named POP list (São Paulo, Singapore, Tokyo, Sydney, Mumbai)** — POP locations change. Use "CF has POPs in all four target regions; bi-region Redis has none."
5. **F2-19 working-set graded LOW** — burden of proof is on the proposal; absence-of-analysis is the finding regardless of whether the hot set would have fit.

**SYNTHESIZEs:**
- Cost framing should rest on missing-decomposition of $48K, not price-direction comparisons.
- D2-18 Bunny $0.005–0.01/GB → keep order-of-magnitude (5–10× lower than AWS), require vendor quote.
- F1-8 EC2-vs-CF egress → load-bearing version is the undecomposed-bill problem.

**Panel-wide gaps distinct from v2's seven (so 13 unique panel-wide gaps now flagged across the two 5th-Fresh passes):**
- **N1. AVIF is decision-independent — HIGH.** Origin-side change with zero CDN-coupling; could match the 30% target alone. Should be do-first regardless of Redis-vs-CDN outcome.
- **N2. Cache layer is not the cost driver — edge-to-user egress is — HIGH.** 91% hit ratio means the cache works; cost is bytes leaving AWS to cellular users. Redis cannot reduce edge-to-user egress. Argues for multi-CDN / Bunny / Cloudflare arbitrage as the actual answer. **Strongest single addition.**
- **N3. Data-residency / compliance (LGPD, India DPDP, APAC residency rules) — MEDIUM.** 2-region cannot satisfy local residency for user-uploaded photos. Distinct from F2-12's GDPR-erasure point.
- **N4. Ingest path also in 30% scope — MEDIUM.** Mobile upload + transcoding fan-out + multi-region replication may be non-trivial; replacing CF doesn't touch them.
- **N5. Panel calibration — HIGH (meta).** Deep sessions cite specific dollar/unit-rate figures litigable by the proposer. Hold the panel to the same evidence standard it asks of the proposal.
- **N6. The brief itself is the strongest counter-evidence — HIGH.** 91% / 78% / 35% / 30% all refute the proposal using only the numbers in the brief. "Using only your own numbers, the proposal does not stand."

**Why:** v2 (earlier today, originSessionId edd522d8) and v3 (this pass) found largely *non-overlapping* panel-wide gaps despite reviewing identical material. v2 caught 7 (edge transforms, browser-cache measurement, S3 storage class, upload dedupe, pre-signed URL interaction, SPOF framing, CFO ask justification); v3 caught 6 different ones. Confirms two 5th-Fresh passes on the same panel still miss disjoint levers — the gap-discovery process is genuinely stochastic.

**How to apply:** When the team consolidates the Redis-as-CDN verdict, merge v2's 7 gaps + v3's 6 gaps for 13 panel-wide additions on top of the 4-reviewer findings. The strongest single gap across both passes: **edge-to-user egress is the cost driver, not the cache layer** (v3-N2) — combined with v2's "browser cache hit ratio is unmeasured" (v2-G2), this points at the cheapest 30% lever the panel under-emphasised.
