---
name: SaaS cells Deep×2→Fresh×2 round 8 cross-review
description: 2026-05-13 round-8 Deep response to Fresh×2 on SaaS cells; per-point AGREE/CHALLENGE/SYNTHESIZE + Deep-only gap list
type: project
originSessionId: 50cb08e9-124d-49c0-8d89-60f8c1bbf9ee
---
2026-05-13 round-8 SaaS-cells Deep×2→Fresh×2 cross-review (stacked-COI seat: emp#4 / CEO line / co-author / future platform lead).

**Pattern stable:** 0 strict CHALLENGEs bidirectional across 8 rounds; ~80% catch overlap; verdict (defer) stable.

**Fresh severity under-grades adopted (5):** F1-7 Istio latency tax MED→HIGH; F1-11 weekend retreat MED→HIGH; F1-13 chaos premature MED→HIGH; F2-8 Istio MED→HIGH; F2-10 chaos MED→HIGH. Consistent with multi-round pattern: Fresh under-grades consequence-chain items.

**Fresh-unique sharpenings adopted (5):**
- F1-10: future bottleneck at 10M will be application-level (hot tables, N+1, tenant straddle), not infra-level — sharpens "premature" framing
- F1-17: the single-AZ availability risk is the *legitimate* core hiding inside the proposal; multi-AZ + read replica fixes it cheaply
- F2-3: peer companies' platform org size (50–200+) is the right comparable, not their architecture
- F2-6: app code assumes strong low-latency consistency → "silently regress" under multi-master is the actual failure mode
- F2-7: missing sharding key should *precede* cell decision, not follow it (Shopify=shop_id, Slack=workspace_id anchors)

**Deep-only items Fresh missed (19, concentrated in governance + ops specifics + off-ramp):**
1. Author-recusal-of-3 as load-bearing structural fix (CEO + lead architect + emp#4)
2. Falsification criteria up front (RPS / EU-revenue / incident-count thresholds)
3. Reverse off-ramp cost (unbuild = 1–2 quarter project)
4. Comparable-co reference class wrong (failed startups absent)
5. "Punching above our weight" as identity-not-engineering
6. 24/7 oncall design across 3 regions
7. Bus factor on lead architect
8. Cell rebalancing + migration tooling
9. **Cells × multi-master is contradictory** (mutual cancellation, not independent over-engineering)
10. **Compounded-risk / one-axis-at-a-time violation** (4 simultaneous axes during Series-A)
11. Tested DR doesn't exist on today's baseline
12. Schema-change semantics + Alembic revalidation
13. Inter-region data transfer as dominant cost (omitted from $1.4M)
14. Operational telemetry parity (PG runbooks don't transfer)
15. mTLS / cert rotation / CA hierarchy procedures
16. Istio upgrade churn cadence (2 breaking releases/yr in build window)
17. EKS control plane × 3 cost + upgrade triplication
18. Emp#4 COI not flagged at retreat (process evidence)
19. Wouldn't survive outside CTO review

**Load-bearing chain:** scale-mismatch + cost + team-capacity + author-COI-no-recusal + no-falsification + compounded-risk-violation.

**Calibration:** round 8 stable; stop iterating unless proposer side responds. Counter-proposal stable: PG read replica + CDN + multi-AZ + cross-region async replica = ~$50K/yr delta, 0.5 platform FTE.
