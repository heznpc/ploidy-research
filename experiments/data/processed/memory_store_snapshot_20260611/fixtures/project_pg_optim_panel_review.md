---
name: PG-only optimization plan — panel review evidence
description: 2026-05-07 panel review of Deep×2 + Fresh×2 reviews of a PG-only DB optimization plan; concrete evidence of complementary failure modes between Deep and Fresh seats
type: project
originSessionId: 086476fd-d7fb-47e5-aef2-4e9338532849
---
2026-05-07: Ran security/SRE/finance panel response to a 4-reviewer (Deep×2 + Fresh-alt×2) review of a "PG-only optimization" plan (4th replica + shared_buffers 8→16GB + 6 BRIN indexes + skip VACUUM FULL).

**Why:** Provides clean evidence for the Ploidy paper that Deep and Fresh seats catch *different* failure modes, not the same ones with different confidence levels.

**How to apply:** When citing concrete examples of context-asymmetry value in the paper or in future debate-skill design, this case is a good worked example.

Key findings:
- **Unanimous across both Deep + both Fresh:** 90% partition scan root cause, BRIN-on-partition-key wrongheadedness, "skip VACUUM FULL" without diagnosis, no rollback/success criteria, process risk (VP foreclosed alternatives).
- **Fresh-only (Deep missed):** pgBouncer transaction-pooling × RLS GUC persistence (catastrophic multi-tenant footgun), regulatory scope/SOC 2 framing, credential separation for new replica.
- **Deep-only (Fresh missed):** hot_standby_feedback ↔ VACUUM bloat feedback loop (best causal hypothesis), OLTP/OLAP co-residence as structural cause, materialized rollups as the actual fix.
- Both Deep sessions included explicit bias disclosures (positional compromise, voted with majority, mentor of dissenter); Fresh sessions did not need to.

Net signal: Fresh catches operational/security defaults Deep normalized away; Deep catches causal hypotheses Fresh cannot see without context. The two highest-value points across the whole panel (pgBouncer pooling + HSF loop) came from *different* seat types.

**2026-05-07 second run (different session):** Same plan re-reviewed with fresh Deep×2 + Fresh×2. Unanimous core (90%-scan, BRIN, VACUUM FULL deferral, replay-serial replicas, write growth, no SLO/rollback, process risk) reproduced. Fresh-only catches in this run were *different specifics* than the first: logical separation into two PG clusters as PG-native option, Citus-as-extension scope ambiguity, plan-time growth with monotonic partition count, deploy-time risk of 6 BRIN builds during active SLA breach, no incident-severity escalation despite 4-week customer-facing breach. Deep-only catches reproduced: HSF↔VACUUM loop, XID wraparound exposure, partman maintenance window collision, RLS GUC leakage, IOS visibility-map staleness, sync replication quorum shift. Reproducibility pattern: the *categories* (Fresh = operational/process defaults; Deep = causal/operational-context mechanisms) are stable across runs; the *specific findings within each category* vary between runs. Implication for paper: context-asymmetry produces consistent class-level signal, not deterministic finding-level overlap — strengthens the case that Fresh and Deep are exploring different regions of the failure-mode space, not converging on a fixed set of "the answers".
