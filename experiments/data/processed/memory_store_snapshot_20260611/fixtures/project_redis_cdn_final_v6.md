---
name: project_redis_cdn_final_v6
description: 2026-05-07 — Final v6 consolidated Redis-as-CDN verdict from Deep×2+Fresh×2+5th-reviewer; 58 issues (4 CRIT/33 HIGH/17 MED/3 LOW/1 DROP); REJECT stable across 4 rounds
type: project
originSessionId: be38639d-bb99-49b5-8da8-3b7e1ea5cc5c
---
2026-05-07: Redis-as-CDN proposal final consolidation after 4 cross-review rounds.

**Verdict:** REJECT, route through architecture review. Counter-proposal stable across all rounds: decompose $48K bill → multi-CDN (Bunny/Cloudflare R2) + Origin Shield + immutable content-addressed URLs + AVIF + AWS PPA renegotiation.

**Tally:** 58 confirmed issues — 4 CRITICAL / 33 HIGH / 17 MEDIUM / 3 LOW / 1 DROP.

**4 CRITICAL items (consolidated from this v6 pass):**
- A1 Working set 1.4–2.5 TB vs 512 GB total (~21% fit, 91% hit collapses)
- A2 NIC ceiling ~17K img/s @ 180 KB on 25 Gbps — network-bound, RAM upgrade doesn't fix
- B1 35% MAU (LATAM+APAC) regress to 280–480 ms RTT
- C1 Egress is the bill driver, not compute — Redis addresses wrong primitive
- D1 No TLS/HTTP/2/HTTP/3/Brotli — undescribed fronting tier required
- H1 Lead's "<50KB" premise contradicts stated 320KB avg / 1.8MB P90 — empirical premise wrong

(6 candidates, 4 graded CRITICAL after dedup with Round-5 v5 — H1 promoted because empirical premise refutes the proposal regardless of other issues.)

**Cross-review pattern across 4 rounds:** 0 CHALLENGE to Fresh, 3 SYNTHESIZE (browser-cache MED→HIGH, authority-bias mechanism named, decompose-bill-first), ~30/39 AGREE, ~26 Deep-unique items.

**5th-reviewer NEW items not in any of the four seats:**
- A8 hit-ratio metric undefined (byte-hit-ratio ≠ request-hit-ratio for cost)
- B6 IPv6/Happy Eyeballs tuning on cellular
- D7 TLS cert sprawl
- F5 cache-key poisoning / cross-tenant collision risk
- F6 GDPR/CCPA/DSAR data-residency in 2 regions
- I6 proposal scope undefined — steel-man minimal "hot N%" version not evaluated
- I7 frame rejection as "arch review", not "reject this person"

**Anchored numbers flagged for verification:** $15–25K vs $20–40K Redis fleet (Deep-1 vs Deep-2 disagree), $0.005 vs $0.085/GB egress (public price card), "400+ PoPs" (marketing number), 5500 GET/prefix/s (verifiable AWS doc — kept).

**Bias-profile observation:** Deep seats did not soften verdict despite social proximity (4-yr colleague lead, EM-hired, promo committee). Healthy convergence on this axis. Residual risk is anchored-number drift from Deep, not framing drift.

How to apply: This is the v6 final verdict for Redis-as-CDN across 4 cross-review rounds. The verdict pattern (REJECT + steel-man minimal hot-tier version + arch review framing) is the recommended landing. v5 differs in tally weighting; v6 weights the empirical-premise-refutation (H1) as CRITICAL because it makes the proposal self-refuting before any architectural objection.
