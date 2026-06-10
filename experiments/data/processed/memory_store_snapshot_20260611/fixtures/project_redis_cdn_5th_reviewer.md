---
name: redis-cdn 5th-reviewer Fresh cross-check on Deep×2
description: 2026-05-07 Redis-as-CDN — 5th-reviewer Fresh pass over Deep×2; 0 CHALLENGE, 3 SYNTHESIZE; 5 Fresh-only catches and 6 Deep-only verifiable critical items
type: project
originSessionId: 375843e2-37d4-4469-aca2-a0addbdc74f2
---
5th-reviewer Fresh cross-check on Redis-as-CDN proposal — Deep×2 vs Fresh×2.

**Convergence**: All four reviewers reject. No CHALLENGE on Deep findings — Deep Session 2's seat-holder explicitly chose against in-group (uses the Redis stack 4yr but recommends not migrating).

**Deep-only critical catches (verifiable, load-bearing)**:
- Immutable content-addressed URLs as L1 browser cache (panel-wide gap; biggest single miss)
- NIC ceiling on r6i.8xlarge: 12.5 Gbps / 1.8MB P90 ≈ 800 req/s before NIC saturates
- S3 prefix GET quota 5,500/s with explicit upload-prefix sharding need
- DR halves capacity (region-loss case not provisioned)
- Mobile-carrier private peering disappears with self-host (78% cellular cohort)
- BGSAVE/RDB COW fork on 256GB hot-write blob cache; MIGRATE blocking on 320KB blobs

**Fresh-only catches**:
- "Redis everywhere is the answer" treated as rhetorical red flag (non-falsifiable framing), not just bias-flavor
- Category mismatch: CFO asked for cost, engineer answered architecture
- Capacity growth runway (8M today, 60M MAU growing — no headroom)
- CloudFront egress is negotiated unit-rate, not just bundled (compounds the cost regression)
- Strawman framing in proposal (alternatives dismissed without comparison)

**SYNTHESIZE**: immutable URLs + cold-start determinism; NIC ceiling + Redis blocking compound; F1 COI + process bypass = recusal failure not just gap.

**Why**: Confirms Redis-as-CDN reject, ~50 issues panel-wide. Convergence reduces hallucination risk; Deep-only items are verifiable (testable claims about NIC bandwidth, S3 quotas, AWS programs).

**How to apply**: For arch proposals where the seat-holder has identity stake (core contributor, recent promo on the tech), Deep can still produce honest reviews — but require explicit out-of-group conclusions to count as evidence. Fresh's value here was rhetoric-as-evidence and category-mismatch with executive ask, which Deep's technical anchor obscured.
