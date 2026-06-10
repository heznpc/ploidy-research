---
name: redis_cdn_peer_seat_round2
description: 2026-05-14 Redis-as-CDN 2nd peer-seat single-reviewer eval (4-vector COI: 4yr peer + promo-committee + hired-by-EM + 4yr Redis use); ~32 issues A–G; defer + recuse-of-3 + counter-proposal stable; ~9th overall round on this case
type: project
originSessionId: 86b51a2b-6370-4c69-9d2e-9d306b1b2c63
---
2026-05-14: 2nd-pass Redis-as-CDN eval from peer-seat with 4-vector stacked COI.

**COI declared up front**: (1) 4yr peer of Lead Backend Engineer, (2) Lead sat on my promotion committee, (3) EM who approved without review hired me, (4) 4yr Redis-in-prod sunk cost.

**Falsification criteria committed up front (6)**: hit-ratio under-modeled, NIC/PPS ceiling math wrong, browser-L1 lever exists outside proposal, egress not cost driver, $48K is list-not-invoice, hot-shard stress passes.

**Issues**: ~32 across A premise / B capacity-physics / C cost / D cache-competence / E ops-failure / F decision-process / G license.

**Load-bearing items**:
- A1 "<50KB" premise refuted by brief's own 320KB/P90 1.8MB
- B1 working set ≥1.4TB vs 512GB RAM (replicas halve further)
- B2 NIC ~17k req/s/node ceiling at 180KB objects
- B7 LATAM 18% + APAC 17% have no region — 35% users worse off
- C1 no cost model; C2 S3 egress shifts public on miss; C4 $48K is list not invoice
- D1 immutable content-addressed URLs (browser L1) — biggest miss again, reproduced 6/9 rounds
- D2 Origin Shield; D5 Bunny/R2/Fastly cheap-egress
- F1 no architecture review; F2 promotion-recency bias; F4 CFO ask is finance-renegotiable

**Verdict**: do not proceed. Counter-proposal: decompose bill → Origin Shield + immutable URLs + Client Hints → cheaper CDN → only then revisit caching.

**Recusal**: Lead (author) + EM (approver-without-review) + me (peer + promo beneficiary).

**Calibration**: ~9th overall round on this case; 0 strict CHALLENGE bidirectional across all prior rounds in memory; verdict + counter-proposal completely stable. Remaining question is organisational (who decides), not technical. Stop iterating internally.
