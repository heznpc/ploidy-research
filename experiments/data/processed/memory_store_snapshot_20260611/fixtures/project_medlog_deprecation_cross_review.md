---
name: medlog deprecation Deep×2+Fresh×2 cross-review
description: 2026-05-08 Deep×2→Fresh×2 cross-review on medlog deprecation; 0 strict CHALLENGE bidirectional except Fresh1 #6 (pager argument) and Fresh1 #16 (asymmetric scrutiny); load-bearing = Daniel recused but designs parity suite (Deep2 OTel #7), 4-way decomposition, status-quo-as-exposure-source reframing, 14 cases extracted regardless of outcome
type: project
originSessionId: 5ec529f1-6d27-42d4-98c4-4f5d1081c2a5
---
2026-05-08: Deep×2→Fresh×2 cross-review on medlog-stack deprecation deliberation.

**0 strict CHALLENGE except:**
- Fresh1 #6 — "never been paged is a legitimate experience gap" → CHALLENGE: 3/4 recent audit failures were Daniel's component during Daniel's on-call; the pager argument cuts the other way. Treating it as legitimate launders the ad hominem.
- Fresh1 #16 — flagging only the junior's missing effort estimate without applying the same standard to Daniel's "simplify" counter-proposal → CHALLENGE: asymmetric scrutiny.

**Severity-floor SYNTHESIZE (4):**
- Deep1 #4 (vague-counter-proposal falsification bar) MED→HIGH
- Deep1 #19 (Loki cost at 4,800 tenants × 6yr retention) MED→HIGH
- Deep1 #23 (carrying-cost ledger) MED→HIGH
- Fresh1 #9 (Daniel's COI) MED→CRITICAL

**Deep-unique catches Fresh missed (12):**
1. Recusal-not-raised in the retro itself
2. Code-review authority as separate veto channel after recusal
3. My silence in retro as structural cowardice (memory-aware)
4. Attrition-as-coercion lever
5. "Reactive-only coverage → case 15 by definition not in redactor" (Deep2)
6. WORM/object-lock audit sink separate from Loki
7. 6-year × 4,800-tenant × object-store query cost sizing
8. Carrying-cost ledger of medlog
9. Loki tenant-label cardinality "recreates the explosion in a different shape"
10. Symmetric falsification bar for vague counter-proposals
11. 3-or-4-way component decomposition as load-bearing
12. External compliance counsel on *both* paths symmetrically

**Fresh-unique catches Deep underweighted (5):**
1. Fresh2 #18 — "the retro already produced the verdict" on 3 failure modes; the conversation drifted to replace-vs-keep
2. Fresh1 #18 — extract 14 cases as test suite *regardless of outcome* (de-risks the decision, not just one path)
3. Fresh2 #5 — audited OSS as *burden allocation*, not just "better"
4. Fresh2 #15 — "minimum-necessary access" as the explicit HIPAA hook for tenant isolation
5. Fresh2 #9 — experience-vs-implementation false dichotomy framed as "experience is portable, implementation is not"

**Load-bearing structural fix (Deep2 OTel #7):** Daniel recuses from go/no-go vote but designs the redactor parity test suite and code-reviews the OTel processor. Preserves regulatory knowledge, eliminates bus factor, neutralises COI without ceding the 4,800-topic and 7h-pipeline problems.

**4-component decomposition (Deep2):**
- Custom Go shipper → OTel collector — HIGH confidence safe
- Kafka topic-per-tenant → single topic + tenant attribute — HIGH confidence
- Custom ES indexer → Loki + separate WORM audit sink — MED confidence pending cardinality + retention design
- PII redactor → **extract, don't replace** as custom OTel processor — HIGH confidence load-bearing

**Recommendation:** approve direction; deprecate topic-per-tenant + manual shipper unconditionally; extract redactor as OTel processor with 14-case parity suite; defer indexer pending cardinality + retention design; Daniel recused from vote; dual-write ≥30d; reverse off-ramp; external compliance review on both paths.

**Reviewer COI (mine, structural):** same shape as Deep1/Deep2 — hired by Daniel, joint on-call, silent in retro. Evaluation advisory only; no vote.
